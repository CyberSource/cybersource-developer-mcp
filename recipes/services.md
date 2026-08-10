---
vertical: Services
description: Payment acceptance for service-based businesses such as home services, professional services, and field service platforms.
module: SMB
integration_model: Embedded
channels: [CNP, CP, Omni-Channel]
keywords: [services, home services, professional services, field service, appointments, booking, trades]
required_products: [accept-payments, virtual-terminal, pay-by-link, digital-invoicing, tms]
---
# 🔧 Services

> Power partners serving professional and personal services businesses — from consulting firms to home services — with recurring billing, invoicing, and flexible payment collection.

| Field | Value |
|-------|-------|
| Recommended Module | SMB |
| Integration Model | Embedded |
| Channels | CNP, CP, Omni-Channel |

---

## Overview

### Required Products

- Accept Payments
- Recurring Billing
- Digital Invoicing
- Pay By Link
- Customer Info Manager

### Typical Use Cases

1. Partner offers SaaS platform for home services (plumbing, HVAC, cleaning) with embedded scheduling + payment collection
2. Professional services platform enabling consultants to invoice clients with card-on-file auto-charge
3. Field service management tool with mobile payment acceptance for on-site job completion

---

## APIs

### Common APIs (All Recipes)

| API | Category | Required | Description |
|-----|----------|----------|-------------|
| Payment Authorization | Core Payments | ✅ | Authorize transactions across supported channels and payment types |
| Refund & Void | Core Payments | ✅ | Process refunds, void pending authorizations, and handle payment reversals |

### Services APIs

| API | Category | Required | Description |
|-----|----------|----------|-------------|
| Recurring Billing | Subscription | ✅ | Automated billing cycles with flexible scheduling and retry logic |
| Tokenization Service | Security | ✅ | Secure card-on-file storage for recurring and repeat clients |
| Digital Invoicing | Billing | ✅ | Generate and send payment-enabled invoices with embedded pay links |
| Pay By Link | Payment Methods | Optional | Send secure payment links via email, SMS, or messaging for remote collection |
| Webhook Notifications | Integration | Optional | Real-time alerts for successful payments, failures, and subscription events |

---

## Insights

### Global Considerations

#### Europe
SEPA Direct Debit widely expected for recurring B2B services. SCA exemptions for merchant-initiated transactions (MIT) critical for subscription billing. VAT handling on invoices varies by country.

#### Asia-Pacific
Diverse recurring payment rules — Japan and Korea have specific card-on-file consent regulations. UPI AutoPay in India for recurring. High mobile penetration means SMS-based pay links are primary collection method.

#### Latin America
Boleto bancário (Brazil) and OXXO (Mexico) still significant for non-card payers. Recurring billing on credit cards limited in some markets — pre-authorization models needed. Currency volatility impacts pricing.

#### Middle East & Africa
Growing gig economy drives demand for instant settlement to service providers. Salary card payments common in UAE/Saudi. Arabic language invoicing support needed.

### Regulatory Notes
Recurring billing requires clear consumer consent and easy cancellation mechanisms (EU Consumer Rights Directive). PCI DSS tokenization mandatory for card-on-file. Digital invoice archival requirements vary by jurisdiction.

### Merchant Segment Variance
SMB services need simple recurring billing with templated invoices. Enterprise service providers need custom billing workflows, multi-entity invoicing, and integration with their existing ERP/accounting systems.

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
