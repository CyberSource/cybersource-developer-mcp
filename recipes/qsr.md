---
vertical: QSR (Quick Service Restaurants)
description: Fast in-store and digital acceptance for quick-service restaurant chains and food ordering platforms.
module: Enterprise
integration_model: Embedded
channels: [CNP, CP, Omni-Channel]
keywords: [qsr, restaurant, food, quick service, fast food, ordering, delivery, kiosk, dining]
required_products: [card-present, accept-payments, unified-checkout, mobile-payments, decision-manager]
---
# 🍔 QSR

> Enable partners to power fast-service restaurant payment platforms — supporting in-store tap-to-pay, mobile ordering, drive-through, kiosk, and delivery with sub-second authorization.

| Field | Value |
|-------|-------|
| Recommended Module | Enterprise |
| Integration Model | Embedded |
| Channels | CNP, CP, Omni-Channel |

---

## Overview

### Required Products

- Accept Payments
- Mobile Payments
- Fraud Management
- Customer Info Manager
- Account Updater

### Typical Use Cases

1. QSR platform partner powers 3,000+ franchise locations with unified POS, mobile ordering, and drive-through payment across 5 markets
2. Self-service kiosk solution provider integrates contactless payment with dynamic menu and upsell at the point of order
3. Mobile ordering platform enables order-ahead with tokenized payment and loyalty integration across QSR brands

---

## APIs

### Common APIs (All Recipes)

| API | Category | Required | Description |
|-----|----------|----------|-------------|
| Payment Authorization | Core Payments | ✅ | Authorize transactions across supported channels and payment types |
| Refund & Void | Core Payments | ✅ | Process refunds, void pending authorizations, and handle payment reversals |

### QSR APIs

| API | Category | Required | Description |
|-----|----------|----------|-------------|
| Tap to Pay | Payment Methods | ✅ | Contactless card and mobile wallet acceptance optimized for speed at counter and drive-through |
| Tokenization Service | Security | ✅ | Token-based mobile ordering and stored payment for loyalty-linked repeat purchases |
| Digital Wallet Integration | Payment Methods | ✅ | Apple Pay, Google Pay, and regional contactless wallets for tap-and-go ordering |
| Fraud Management | Risk | ✅ | Low-friction fraud screening optimized for QSR transaction patterns and values |

---

## Insights

### Global Considerations

#### Europe
Contactless adoption extremely high (95%+ in UK, Netherlands, Nordics). SCA exemptions for low-value contactless. Multi-currency for pan-European QSR chains. Local payment method support varies — iDEAL for kiosk in Netherlands, Swish in Sweden.

#### Asia-Pacific
QR-code payment dominant in China, Singapore, Southeast Asia — must support alongside NFC contactless. Super-app ordering (Grab, Line, WeChat) creates payment platform dependencies. High mobile ordering penetration. Multi-market franchise management complex.

#### Latin America
Cash still significant for QSR in many markets — hybrid cash+card POS needed. Contactless growing rapidly in Brazil and Mexico. PIX for mobile ordering in Brazil. Voucher/meal card acceptance (Vale Refeição in Brazil) is a must.

#### Middle East & Africa
Contactless adoption high in UAE and Saudi. mada contactless mandatory in Saudi. Drive-through dominant channel in Gulf QSR. Delivery-heavy market — payment must integrate with local aggregators (Talabat, Careem).

### Regulatory Notes
Contactless transaction limits vary by market (raised post-COVID but still market-specific). Tipping regulations impact payment flows in some jurisdictions. Franchise disclosure rules affect payment system terms. Food service licensing may impact MCC assignment.

### Merchant Segment Variance
SMB single-location QSR needs simple countertop POS with contactless. Enterprise QSR chains need multi-channel orchestration, franchise hierarchy management, cross-market currency/compliance handling, and integration with back-of-house restaurant management systems.

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
