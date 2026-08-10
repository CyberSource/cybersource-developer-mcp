---
vertical: Travel & Airlines
description: High-value, multi-currency acceptance for airlines and travel platforms with complex fraud and settlement needs.
module: Enterprise
integration_model: API
channels: [CNP, Omni-Channel]
keywords: [travel, airline, airlines, flights, booking, hospitality, hotel, tourism, multi-currency]
required_products: [accept-payments, decision-manager, tms, reporting, transaction-search]
---
# ✈️ Travel & Airlines

> Enable partners to build payment platforms for travel agencies, airlines, and hospitality — supporting complex itinerary payments, multi-currency, ancillary sales, and high-value transactions.

| Field | Value |
|-------|-------|
| Recommended Module | Enterprise |
| Integration Model | API |
| Channels | CNP, Omni-Channel |

---

## Overview

### Required Products

- Accept Payments
- Fraud Management
- Pay By Link
- Customer Info Manager
- Account Updater

### Typical Use Cases

1. OTA platform partner enables 200+ travel agencies to sell flights, hotels, and packages with multi-currency checkout and split settlements
2. Airline ancillary commerce platform — seat upgrades, bags, lounge access — all tokenized to original booking payment
3. Group travel platform enables tour operators to collect deposits, milestone payments, and final balances across multi-month booking timelines

---

## APIs

### Common APIs (All Recipes)

| API | Category | Required | Description |
|-----|----------|----------|-------------|
| Payment Authorization | Core Payments | ✅ | Authorize transactions across supported channels and payment types |
| Refund & Void | Core Payments | ✅ | Process refunds, void pending authorizations, and handle payment reversals |

### Travel & Airlines APIs

| API | Category | Required | Description |
|-----|----------|----------|-------------|
| Multi-Currency Pricing | Global | ✅ | Display prices in traveller's currency, settle in merchant's currency. Support 150+ currencies |
| 3D Secure 2 | Security | ✅ | Strong Customer Authentication with risk-based exemptions for low-friction high-value travel bookings |
| Fraud Management | Risk | ✅ | Travel-specific fraud rules — velocity checks, geo-mismatch, booking pattern analysis |
| Tokenization Service | Security | ✅ | Tokenize traveller payment credentials for multi-leg and ancillary purchases throughout trip lifecycle |
| Pay By Link | Payment Methods | Optional | Payment links for travel agent bookings, group travel deposits, and ancillary upsells |
| Webhook Notifications | Integration | Optional | Real-time payment status for booking confirmation, schedule changes, and cancellation flows |

---

## Insights

### Global Considerations

#### Europe
PSD2/SCA with travel-specific exemptions (MIT for ancillaries, TRA for trusted travellers). Strong preference for local payment methods — iDEAL (NL), Bancontact (BE), Klarna (Nordics). EU261 refund regulations create complex payment reversal requirements.

#### Asia-Pacific
Diverse local payment methods critical for conversion — Alipay/WeChat (China), PayPay (Japan), GrabPay (SEA). Multi-currency essential — APAC travellers book across dozens of currencies. Regulatory complexity for cross-border travel payments.

#### Latin America
Installment payments on credit cards essential — 6-12 month plans for travel purchases. High fraud risk requires advanced screening. Currency controls in Argentina, Brazil impact cross-border travel payments. Boleto for non-card travel bookings in Brazil.

#### Middle East & Africa
Growing outbound travel market from Gulf states — high-value transactions. Multi-currency critical for UAE's international traveller base. Turkey is a major travel market with Lira volatility considerations. Hajj/Umrah travel creates seasonal payment spikes.

### Regulatory Notes
IATA regulations for airline payment processing. EU Package Travel Directive impacts multi-component bookings. Anti-fraud requirements higher for travel (CNP, cross-border, high-value). PCI DSS with additional travel industry requirements.

### Merchant Segment Variance
SMB travel agencies need simple booking-and-pay flows with standard cancellation handling. Enterprise airlines and OTAs need complex multi-leg payment orchestration, dynamic pricing integration, loyalty point + card hybrid payments, and GDS connectivity.

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
