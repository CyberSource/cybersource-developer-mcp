---
vertical: Fitness
description: Membership billing, class/session payments, and retail POS for gyms, studios, and wellness businesses.
module: SMB
integration_model: Embedded
channels: [CNP, CP]
keywords: [fitness, gym, studio, wellness, membership, trainer, class, yoga, health club, subscription]
required_products: [accept-payments, recurring-billing, account-updater, customer-info-manager, mobile-payments, tms]
---
# 💪 Fitness

> Empower partners building platforms for gyms, studios, and wellness businesses with membership billing, class/session payments, and retail POS for merchandise.

| Field | Value |
|-------|-------|
| Recommended Module | SMB |
| Integration Model | Embedded |
| Channels | CNP, CP |

---

## Overview

### Required Products

- Accept Payments
- Recurring Billing
- Account Updater
- Customer Info Manager
- Mobile Payments

### Typical Use Cases

1. Gym management platform serves 500+ franchise locations with centralized membership billing and location-level settlement
2. Boutique studio booking app integrates class-pack purchases with auto-renewing membership billing
3. Wellness marketplace enables independent trainers to accept session payments with embedded checkout

---

## APIs

### Common APIs (All Recipes)

| API | Category | Required | Description |
|-----|----------|----------|-------------|
| Payment Authorization | Core Payments | ✅ | Authorize transactions across supported channels and payment types |
| Refund & Void | Core Payments | ✅ | Process refunds, void pending authorizations, and handle payment reversals |

### Fitness APIs

| API | Category | Required | Description |
|-----|----------|----------|-------------|
| Recurring Billing | Subscription | ✅ | Automated membership billing with freeze, upgrade, and cancellation support |
| Tokenization Service | Security | ✅ | Secure card-on-file for membership auto-renewal and stored payment credentials |
| Account Updater | Lifecycle | ✅ | Automatically update expired or reissued cards to prevent involuntary membership churn |
| Payment Capture | Core Payments | Optional | Auth-capture for class bookings with no-show fee policies |

---

## Insights

### Global Considerations

#### Europe
Consumer protection requires easy cancellation (EU Unfair Commercial Practices Directive). SCA exemptions for merchant-initiated recurring transactions. SEPA as alternative to card-on-file recurring. VAT on fitness services varies (exempt in some markets, standard rate in others).

#### Asia-Pacific
ClassPass-style aggregator models dominant in APAC urban markets. UPI Autopay for recurring in India. Multi-gym chain models span ASEAN requiring multi-currency. High mobile-first booking — payment must be seamless in-app.

#### Latin America
Credit card installments needed for annual membership pre-pay. High churn in fitness — Account Updater and retry logic critical. PIX gaining ground for gym payments in Brazil. Informal fitness sector means simplified onboarding needed.

#### Middle East & Africa
Gender-segregated facilities common — multi-location management with distinct branding. Growing premium fitness market in Gulf states. Ramadan/seasonal billing adjustments needed. Corporate wellness programs driving B2B billing.

### Regulatory Notes
Subscription auto-renewal disclosure required in most jurisdictions. Cooling-off periods for gym memberships (varies by market). PCI DSS for stored card credentials. Consumer cancellation rights impact billing flow design.

### Merchant Segment Variance
SMB independent gyms need plug-and-play membership billing with pre-built templates. Enterprise fitness chains need multi-location hierarchy, custom billing rules per brand, corporate membership billing, and advanced reporting.

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
