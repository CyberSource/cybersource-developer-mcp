---
vertical: Healthcare
description: Patient payment platforms for healthcare providers — copays, insurance billing, payment plans, HSA/FSA, and telehealth payments with strict data compliance.
module: SMB
integration_model: API
channels: [CNP]
keywords: [healthcare, patient, copay, medical, dental, telehealth, hsa, fsa, hospital, insurance billing]
required_products: [accept-payments, tms, recurring-billing, pay-by-link, digital-invoicing]
---
# Healthcare

> Enable partners to build patient payment platforms for healthcare providers — covering copays, insurance billing, payment plans, HSA/FSA, and telehealth payments with strict data compliance.

| Field | Value |
|-------|-------|
| Recommended Module | SMB |
| Integration Model | API |
| Channels | CNP |

---

## Overview

### Required Products

- Accept Payments
- Customer Info Manager
- Recurring Billing
- Pay By Link
- 24/7 Support

### Typical Use Cases

1. Practice management platform enables 1,000+ dental/medical offices to collect patient payments with automated insurance copay calculation
2. Telehealth platform integrates payment collection at the point of virtual visit — copay before, balance after
3. Hospital system partner offers patient payment plans for high-deductible treatments with HSA/FSA auto-substantiation

---

## APIs

### Common APIs (All Recipes)

| API | Category | Required | Description |
|-----|----------|----------|-------------|
| Payment Authorization | Core Payments | ✅ | Authorize transactions across supported channels and payment types |
| Refund & Void | Core Payments | ✅ | Process refunds, void pending authorizations, and handle payment reversals |

### Healthcare APIs

| API | Category | Required | Description |
|-----|----------|----------|-------------|
| Tokenization Service | Security | ✅ | Secure card-on-file storage with HIPAA-compliant data handling for patient payment credentials |
| Recurring Billing | Subscription | ✅ | Patient payment plans with configurable installment schedules and automatic collection |
| HSA/FSA Card Support | Payment Methods | ✅ | Accept Health Savings Account and Flexible Spending Account cards with IIAS auto-substantiation |
| Pay By Link | Payment Methods | Optional | Secure payment links for patient billing statements and post-visit balance collection |
| Digital Invoicing | Billing | Optional | Generate patient-facing statements with embedded payment options |

---

## Insights

### Global Considerations

#### Europe
GDPR + national health data regulations (e.g., NHS DSPT in UK). Patient payment responsibility varies dramatically by country (minimal in UK/Nordics, significant in France/Germany). Cross-border healthcare (EU Directive) creates multi-market payment needs.

#### Asia-Pacific
Mixed public-private healthcare models. India Ayushman Bharat creating digital payment infrastructure for healthcare. Japan/Korea have unique health insurance payment flows. Medical tourism (Thailand, Singapore, India) requires multi-currency patient billing.

#### Latin America
Growing private healthcare sector driving patient payment digitization. Installment plans critical for elective procedures. E-prescribing and digital health advancing in Brazil and Mexico. Currency instability impacts payment plan design.

#### Middle East & Africa
Mandatory health insurance in UAE and Saudi creates unique billing flows. Medical tourism significant in UAE, Turkey. Growing telemedicine adoption post-COVID. Arabic language patient billing support needed.

### Regulatory Notes
HIPAA (US), GDPR (EU), PIPEDA (Canada) for health data. IIAS requirements for HSA/FSA acceptance. State-level patient billing regulations (US surprise billing laws). Medical debt collection regulations vary by jurisdiction.

### Merchant Segment Variance
SMB solo/group practices need simple copay collection and basic payment plans. Enterprise health systems need multi-facility billing, complex insurance integration, patient financial assistance workflows, and enterprise reporting across hundreds of providers.

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
