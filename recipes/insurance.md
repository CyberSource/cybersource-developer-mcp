---
vertical: Insurance
description: Premium collection, recurring billing, and refunds for insurance platforms and carriers.
module: SMB
integration_model: API
channels: [CNP, Omni-Channel]
keywords: [insurance, premium, policy, claims, carrier, insurtech, underwriting]
required_products: [accept-payments, recurring-billing, account-updater, echeck, tms]
---
# 🛡️ Insurance

> Enable partners to build premium collection, claims disbursement, and policy payment platforms for insurance carriers and brokers operating across global markets.

| Field | Value |
|-------|-------|
| Recommended Module | SMB |
| Integration Model | API |
| Channels | CNP, Omni-Channel |

---

## Overview

### Required Products

- Accept Payments
- Recurring Billing
- eCheck
- Digital Invoicing
- Customer Info Manager

### Typical Use Cases

1. Insurtech partner enables 50+ insurance carriers to collect premiums via a unified digital platform with multi-payment-method support
2. Broker management system integrates payment collection so brokers can collect and reconcile premiums inline with policy quotes
3. Claims platform automates refund/disbursement to policyholder's original payment method upon claim approval

---

## APIs

### Common APIs (All Recipes)

| API | Category | Required | Description |
|-----|----------|----------|-------------|
| Payment Authorization | Core Payments | ✅ | Authorize transactions across supported channels and payment types |
| Refund & Void | Core Payments | ✅ | Process refunds, void pending authorizations, and handle payment reversals |

### Insurance APIs

| API | Category | Required | Description |
|-----|----------|----------|-------------|
| Recurring Billing | Subscription | ✅ | Automated premium collection with policy-aligned billing cycles |
| eCheck / ACH | Payment Methods | ✅ | Bank account debits for high-value premium payments where card limits apply |
| Tokenization Service | Security | ✅ | Secure storage of payment credentials across policy lifecycle |
| Pay By Link | Payment Methods | Optional | Send payment collection links for policy renewals and outstanding premiums |
| Webhook Notifications | Integration | Optional | Payment status callbacks for policy management system integration |

---

## Insights

### Global Considerations

#### Europe
Insurance premium tax (IPT) varies by country and must be handled in billing. PSD2 SCA applies to policyholder-initiated payments. SEPA Direct Debit is the dominant method for recurring premiums in many EU markets. Solvency II impacts fund segregation requirements.

#### Asia-Pacific
Market-specific insurance regulators (IRDAI in India, MAS in Singapore) have payment collection rules. Mobile-first premium collection in emerging markets. Multi-currency needed for regional insurance groups operating across ASEAN.

#### Latin America
Boleto bancário critical for premium collection in Brazil. Installment plans on credit cards expected. High informality means KYC requirements for policyholders vary. Currency controls impact cross-border premium flows.

#### Middle East & Africa
Takaful (Islamic insurance) requires Sharia-compliant payment structures. Growing digital insurance adoption in UAE and Saudi. Salary assignment for premium collection common in Gulf states.

### Regulatory Notes
Insurance payment regulations require segregated trust accounts in most jurisdictions. Anti-money laundering (AML) requirements for high-value premiums. Data residency requirements for policyholder payment data. Premium financing regulations vary by market.

### Merchant Segment Variance
SMB brokers need simple premium collection with pre-built templates. Enterprise carriers need custom billing engines, multi-entity settlement, regulatory reporting, and integration with policy administration systems.

---

## Integration Path

| Step | Title | Description |
|------|-------|-------------|
| 1 | Sandbox Access | Register on developer portal, obtain sandbox API credentials, and configure test merchant profiles. |
| 2 | Develop | Build your payment integration using CyberSource SDKs and APIs for your chosen channels. |
| 3 | Testing & Validation | Execute test scenarios, validate payment flows, and confirm compliance requirements. |
| 4 | Go Live & Scale | Launch with pilot merchants, monitor performance, and scale across your portfolio. |
| 5 | Merchant Onboarding | Onboard merchants with KYC, bank verification, and product activation. |

---

[← Back to All Recipes](./index.md)
