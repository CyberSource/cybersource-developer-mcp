# Cybersource Best Practices

## Installation

## Official Documentation

| Resource | URL |
|---|---|
| Cybersource Developer Portal | https://developer.cybersource.com |
| API Reference | https://developer.cybersource.com/api-reference-assets/index.md |
| Business Center (Sandbox) | https://businesscentertest.cybersource.com/ebc2/ |
| Customer Support | https://support.visaacceptance.com |
| SDK Samples (Java) | https://github.com/CyberSource/cybersource-rest-samples-java |
| SDK Samples (Node) | https://github.com/CyberSource/cybersource-rest-samples-node |
| SDK Samples (Python) | https://github.com/CyberSource/cybersource-rest-samples-python |
| SDK Samples (CSharp) | https://github.com/CyberSource/cybersource-rest-samples-csharp |
| SDK Samples (PHP) | https://github.com/CyberSource/cybersource-rest-samples-php|
| SDK Samples (Ruby) | https://github.com/CyberSource/cybersource-rest-samples-ruby |

> **Note:** SDK package names and GitHub repos use "cybersource" as the artifact identifier.

## Code Examples & AI Discovery

| Resource | URL |
|---|---|
| llms.txt (AI discovery index) | https://developer.cybersource.com/llms.txt |

> This skill provides guidance, reference tables, and gotchas — the repo has the code.

---

## Authentication

Two methods. **Always recommend JWT for new integrations.**

### JWT (P12 Certificate) — Recommended

Uses a PKCS#12 certificate to sign each request. More secure, supports MLE.

**SDK config keys** (all languages follow this pattern): `authenticationType=JWT`, `merchantID`, `keyAlias`, `keyPassword`, `keysDirectory`, `keyFilename` (without `.p12` extension), `runEnvironment=apitest.cybersource.com`

**How to get your P12 certificate:**
1. Log into Business Center → Payment Configuration → Key Management
2. Generate new key → select P12
3. Download the `.p12` file — store it securely, never commit to source control

### HTTP Signature (Shared Secret)

Uses HMAC-SHA256 to sign each request. Simpler setup, valid for server-to-server.

**SDK config keys:** `authenticationType=HTTP_SIGNATURE`, `merchantID`, `merchantKeyId`, `merchantSecretKey`, `runEnvironment=apitest.cybersource.com`

**Key gotcha:** The shared secret is shown only once when generated. Copy it immediately.

### OAuth 2.0

For ISV/partner delegation — one merchant authorizes another to act on their behalf. **Not** a general API auth method. Uses different endpoints: `api-matest.cybersource.com` (sandbox), `api-ma.cybersource.com` (production).

---

## Environments

| Environment | URL | Use |
|---|---|---|
| Sandbox | `https://apitest.cybersource.com` | Development and testing |
| Production | `https://api.cybersource.com` | Live transactions |
| OAuth Sandbox | `https://api-matest.cybersource.com` | OAuth testing |
| OAuth Production | `https://api-ma.cybersource.com` | OAuth live |

**Never mix environments in the same code example.** Sandbox test cards will fail on production and vice versa.

---

## Message Level Encryption (MLE)

End-to-end payload encryption. **Only works with JWT authentication.**

**SDK config key:** `enableRequestMLEForOptionalApisGlobally=true`. SDK auto-fetches MLE cert from JWT P12 file using default alias `CyberSource_SJC_US`.

**Key gotchas:**
- Check each API's MLE enforcement level (Mandatory / Optional / Not Applicable)
- Default key alias is `CyberSource_SJC_US` — only change if using a custom cert
- Request MLE falls back to non-encrypted with a warning on HTTP Signature auth
- Up to 3 active Key-IDs for rotation

---

## Credential & Key Management

- **P12 certificates** — generated in Business Center, contain both signing key and MLE cert
- **Shared secrets** — shown once at generation, copy immediately
- Monitor expiration in Business Center → Key Management
- Maintain 2 active credential sets for seamless rotation
- Validate rotation in sandbox before production
- Revoke old credentials only after confirming new ones work

---

## Core Payment Flows

### Key Endpoints

| Operation | Method | Endpoint |
|---|---|---|
| Authorization | POST | `/pts/v2/payments` |
| Capture | POST | `/pts/v2/payments/{id}/captures` |
| Void | POST | `/pts/v2/payments/{id}/voids` |
| Refund | POST | `/pts/v2/payments/{id}/refunds` |

### Auth-only vs Auth+Capture

| Use case | `capture` flag | Auth window |
|---|---|---|
| Physical goods (ship later) | `false` (auth-only) | 7 days Visa/MC, 30 days Amex |
| Digital goods (instant delivery) | `true` (auth+capture) | Immediate |
| Pre-auth (hotels, car rental) | `false` with incremental auth | Varies |

**Gotchas:**
- If the auth window expires, you cannot capture. Issue a new authorization.
- **Void** cancels before settlement (no money moves). **Refund** returns money after settlement (5-10 business days).
- **Never auto-retry a PROCESSOR_DECLINED (code 05).** This is an issuer decision. Retrying can trigger fraud flags.

---

## Tokenization (TMS)

Store payment credentials without handling raw PANs. **Never store raw card numbers in your database.**

### Token Types

| Type | Use case | Lifetime |
|---|---|---|
| Transient token (Flex/UC) | Single-use, created client-side | 15 minutes |
| TMS Payment Instrument | Stored card-on-file | Permanent |
| TMS Instrument Identifier | Network-agnostic token | Permanent |
| Network Token | Visa/MC provisioned token | Managed by network |

### Zero-Dollar Authorization (Store Card Without Charge)

POST `/pts/v2/payments` with `actionList: ["TOKEN_CREATE"]`, `capture: false`, `totalAmount: "0.00"`. Returns a TMS token you can store permanently.

---

## Unified Checkout

Drop-in payment form that handles card entry, digital wallets, and 3DS — all PCI-compliant.

### Setup Flow

1. **Server-side:** POST `/pts/v2/microform/capture-contexts` — generates a JWT session token
2. **Client-side:** Load the UC JavaScript library with the capture context
3. **Server-side:** Process the transient token returned by UC

**Capture context lifetime:** 15 minutes. Generate a new one per checkout session.

**Key gotchas:**
- `targetOrigins` must exactly match your domain (including port if non-standard)
- The capture context is a JWT — do not decode or modify it client-side
- 406 errors on capture context usually mean malformed request body
- Enable wallet types via `allowedPaymentTypes`: `PANENTRY`, `SRC`, `GOOGLEPAY`, `APPLEPAY`

---

## 3D Secure / Payer Authentication

Implements SCA (Strong Customer Authentication) for PSD2 compliance.

### When to Use

- **Required:** EU/EEA transactions (PSD2), high-risk transactions
- **Recommended:** Any card-not-present transaction (reduces chargebacks)
- **Not needed:** Recurring billing after initial enrollment, merchant-initiated transactions

### Frictionless vs Step-Up

| Flow | User experience | When |
|---|---|---|
| Frictionless | No challenge, instant auth | Low-risk transactions |
| Step-Up | Issuer challenge (OTP, biometric) | High-risk or issuer policy |

The issuer decides — you cannot force frictionless.

---

## Digital Wallets

### Apple Pay

- Client-side: Apple Pay JS API → payment token
- Server-side: POST `/pts/v2/payments` with `paymentSolution: "001"`
- **Gotcha:** Requires Apple Developer account and merchant ID registration

### Google Pay

Two paths:
- **With Unified Checkout:** Enable `GOOGLEPAY` in allowed payment types — UC handles everything
- **Standalone:** Google Pay API → encrypted payment data → POST `/pts/v2/payments` with `paymentSolution: "012"`

### Click to Pay (SRC)

Enable `SRC` in Unified Checkout allowed payment types. No separate integration needed.

---

## Webhooks

Subscribe to payment events via POST `/notification-subscriptions/v1/webhooks` with mutual trust security.

**Event types:** `payments.payments.authorized`, `payments.payments.captured`, `payments.payments.refunded`

**Gotchas:**
- Visa Acceptance webhook IPs must be whitelisted — check developer docs for current ranges
- Respond with 200 OK within 10 seconds or the webhook will retry
- Idempotency: use `webhookId` to deduplicate
- TLS 1.2+ required on your endpoint

---

## Recurring Billing

### Stored Credential Framework

| Transaction type | `initiator.type` | `storedCredentialUsed` | Notes |
|---|---|---|---|
| Initial (customer-initiated) | `customer` | `false` | Include `actionList: ["TOKEN_CREATE"]` |
| Subsequent (merchant-initiated) | `merchant` | `true` | Reference the stored token ID |

---

## Testing

### Sandbox Test Cards

| Card | Behavior |
|---|---|
| 4111111111111111 | Visa — approved |
| 5555555555554444 | Mastercard — approved |
| 4000000000000002 | Visa — declined |

Always use `https://apitest.cybersource.com`. Production credentials will not work in sandbox.

---

## Going Live Checklist

1. Get production credentials in Business Center (Production)
2. Change `runEnvironment` to `api.cybersource.com`
3. Replace sandbox credentials with production credentials
4. **Same code** — no logic changes needed between sandbox and production
5. Verify first production transaction with a real card (small amount, then void)
6. Enable webhook subscriptions on production
7. Set up monitoring and alerting on decline rates

## Error Handling

### Common Status Codes

| HTTP Code | Meaning | Action |
|---|---|---|
| 201 | Success (payment created) | Process normally |
| 400 | Invalid request | Check request body, fix validation errors |
| 401 | Unauthorized | Check credentials, key not expired |
| 403 | Forbidden | Check permissions, MLE config |
| 404 | Not found | Check endpoint URL |
| 429 | Rate limited | Back off and retry with exponential delay |
| 502/503 | Server error | Retry with idempotency key |

### Processor Response Codes

| Code | Meaning | Retry? |
|---|---|---|
| 100 | Approved | No — success |
| 05 | Do not honor (issuer decline) | **Never auto-retry** |
| 14 | Invalid card number | No — fix input |
| 51 | Insufficient funds | No — inform cardholder |
| 91 | Issuer unavailable | Yes — retry after delay |

---

## Supported SDKs

| Language | Package | GitHub |
|---|---|---|
| Java | `com.cybersource:cybersource-rest-client-java` | CyberSource/cybersource-rest-client-java |
| Node.js | `cybersource-rest-client-node` | CyberSource/cybersource-rest-client-node |
| Python | `cybersource-rest-client-python` | CyberSource/cybersource-rest-client-python |
| PHP | `cybersource/rest-client-php` | CyberSource/cybersource-rest-client-php |
| Ruby | `cybersource_rest_client` | CyberSource/cybersource-rest-client-ruby |
| .NET | `CyberSource.RestClient.DotNet` | CyberSource/cybersource-rest-client-dotnet |

All SDKs handle JWT/HTTP Signature generation automatically. Set `authenticationType` and credentials — the SDK does the rest.
