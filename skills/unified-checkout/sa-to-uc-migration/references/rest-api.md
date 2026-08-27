# Authenticating and calling the CyberSource REST API

Unified Checkout is driven by CyberSource REST calls. Auth is **JWT v2 (HS256 shared secret)** — the deprecated HTTP Signature (`signature:` header) scheme is gone. You write the client in the project's own language; the auth is standard HMAC/SHA-256/base64url, so no third-party JWT library is needed. This doc gives the exact contract — the parts that are non-obvious and must be right.

## Credentials (three values)

| Value | What it is |
|---|---|
| `MERCHANT_ID` | The merchant ID (often the same as the SA merchant). |
| `KEY_ID` | REST **Shared Secret** key id (a UUID). Goes in the JWT header as `kid`. |
| `SECRET_KEY` | Base64-encoded REST shared secret. **Base64-decode it** to get the HMAC key. |

Generate them in Business Center → Payment Configuration → Key Management → Generate Key → **REST – Shared Secret**. The secret is shown once. These are *different* from SA's `access_key`/`profile_id`/SA-secret — SA credentials do not work for REST.

Load them however the project already loads config (see SKILL.md — mirror the existing store; don't impose `.env`). Placeholders are fine to build against; only the live call fails until real values are present.

## The JWT (per request)

**Header:**
```
{ "typ": "JWT", "alg": "HS256", "kid": "<KEY_ID>" }
```

**Payload claims:**
```
iat                     current unix time (seconds)
exp                     iat + 120        (short-lived; regenerate per request)
iss                     <MERCHANT_ID>
jti                     a fresh UUID per request
request-host            the API host (see below), no scheme
request-method          the HTTP method, lowercase (e.g. "post")
request-resource-path   the path only, e.g. "/uc/v1/sessions"
v-c-jwt-version         "2"              (string)
v-c-merchant-id         <MERCHANT_ID>
```
For any request **with a body** (all POSTs), also add:
```
digest                  base64( SHA-256(raw request body bytes) )
digestAlgorithm         "sha-256"
```
The `digest` must be computed over the exact bytes you send — build the body string once, hash that, and send that same string.

**Sign:** `signing_input = base64url(header) + "." + base64url(payload)` (base64url, no `=` padding). `signature = HMAC_SHA256(key = base64_decode(SECRET_KEY), msg = signing_input)`. Token = `signing_input + "." + base64url(signature)`.

**Send:** header `Authorization: Bearer <token>`, `Content-Type: application/json`.

## Hosts / environment

| Env | Host |
|---|---|
| Sandbox/test | `apitest.cybersource.com` |
| Production | `api.cybersource.com` |

`request-host` and the request URL must use the host that matches the credentials. A **401** on an otherwise-correct call almost always means credentials and host are from different environments.

## Calling `POST /uc/v1/sessions`

This endpoint returns a **raw JWT string** (media type `application/jwt`), *not* JSON — don't `.json()` it. Decode the JWT payload (middle segment, base64url) to read `ctx[0].data.clientLibrary` and `ctx[0].data.clientLibraryIntegrity`; hand `{ captureContext: <the raw JWT>, clientLibrary, clientLibraryIntegrity }` to the browser. (Detect it: a JWT is three dot-separated base64url segments and doesn't start with `{`.)

`/pts/v2/payments` (transient-token flow only) returns normal JSON.

## Corporate TLS proxy

Enterprise networks often run a TLS-intercepting proxy whose CA the default trust store doesn't know, so the first CyberSource call fails with `CERTIFICATE_VERIFY_FAILED`. Fix by pointing the HTTP client at the corporate CA bundle:
- Python (`requests`/`urllib`): `REQUESTS_CA_BUNDLE` / `SSL_CERT_FILE`.
- Node: `NODE_EXTRA_CA_CERTS`.

Dev-only last resort: a `VERIFY_SSL=false` style flag that disables verification. **Never in production.**
