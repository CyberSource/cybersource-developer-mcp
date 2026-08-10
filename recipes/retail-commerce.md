---
vertical: Retail / eCommerce
description: Unified in-store and online acceptance for retail merchant portfolios, from single-outlet SMBs to multi-location enterprise chains.
module: Both
integration_model: Embedded
channels: [CP, CNP, Omni-Channel]
keywords: [retail, ecommerce, e-commerce, store, shop, omnichannel, omni-channel, point of sale, pos, marketplace]
required_products: [card-present, virtual-terminal, recurring-billing, unified-checkout, pay-by-link, digital-invoicing, tms, fme, reporting, transaction-search]
---
# 🛒 Retail / eCommerce

> Enable partners to offer unified in-store and online payment acceptance across retail merchant portfolios — from single-outlet SMBs to multi-location enterprise chains.

| Field | Value |
|-------|-------|
| Recommended Module | Both (SMB + Enterprise) |
| Integration Model | Embedded |
| Channels | CP, CNP, Omni-Channel |
| Estimated Timeline | 6–12 weeks |

---

## Overview

### Platform Suitability

| Module | Best For | Contracting | Fraud Option | Timeline |
|--------|----------|-------------|--------------|----------|
| Visa Acceptance SMB | Single/few-location retailers, turnkey integration, ISVs serving SMB portfolios | Fixed product bundle included in merchant contract | FME | 6–8 weeks |
| Visa Acceptance Enterprise | Multi-location chains, complex omni-channel, multi-market, custom checkout | Flexible — solutions build their own product mix | FME or Decision Manager (DM) | 8–12 weeks |

### Always-On Defaults

| Product | Description |
|---------|-------------|
| Payments | Authorization, Capture, Refund/Void |
| Fraud | Transaction-level risk screening |
| Tokenisation | Card data replaced with secure tokens |

### SMB Product Bundle

| Product | Category | Description |
|---------|----------|-------------|
| Card Present (CP) | In-Store Acceptance | Terminal/POS integration, tap-to-pay, chip, contactless |
| Virtual Terminal | Manual Entry / MOTO | Key-entered transactions for phone/mail orders |
| Recurring Billing | Subscription & Repeat | Automated billing cycles, retry logic, dunning |
| Digital Acceptance — Unified Checkout | Online Acceptance | Secure card capture fields (Flex Microform), hosted payment page |
| Digital Acceptance — Pay By Link | Online Acceptance | Secure payment links via email, SMS, messaging |
| Digital Acceptance — Invoicing | Online Acceptance | Payment-enabled invoices with embedded pay links |
| TMS (Token Management Service) | Security & Lifecycle | Token creation, retrieval, update; Network Token lifecycle |
| FME (Fraud Management Essentials) | Risk | Rule-based fraud screening for SMB transaction patterns |
| Reporting | Analytics | Settlement reports, transaction summaries, dispute data. API + Portal |
| Transaction Search | Operations | Query, filter, and export transaction history. API + Portal |

### Required Products

- Card Present
- Virtual Terminal
- Recurring Billing
- Unified Checkout
- Pay By Link
- Invoicing
- TMS
- FME
- Reporting
- Transaction Search

### Typical Use Cases

1. ISV serves 500+ independent retail shops with turnkey POS + online checkout, all products pre-bundled in contract (SMB)
2. Boutique eCommerce platform enables small retailers to accept online payments via Unified Checkout with Pay By Link for social selling (SMB)
3. Partner manages 2,000+ retail merchants across EU and NA with unified reporting, custom fraud rules per region, multi-currency settlement (Enterprise)
4. White-label POS + eCommerce platform for department store chain with custom-branded checkout, loyalty integration, omni-channel tokenisation (Enterprise)

---

## APIs

### Common APIs (All Recipes)

| API | Category | Required | Description |
|-----|----------|----------|-------------|
| Payment Authorization | Core Payments | ✅ | Authorize transactions across supported channels and payment types |
| Refund & Void | Core Payments | ✅ | Process refunds, void pending authorizations, and handle payment reversals |

### Retail / eCommerce APIs

| API | Category | Required | Description |
|-----|----------|----------|-------------|
| Payment Capture | Core Payments | ✅ | Capture authorized payments (full, partial, split) |
| Flex Microform v2 (Unified Checkout) | Digital Acceptance | ✅ | Secure tokenisation — embed card fields without PCI scope |
| Digital Wallet Integration | Digital Acceptance | ✅ | Apple Pay, Google Pay, Click to Pay |
| Pay By Link — Generation & Status | Digital Acceptance | ✅ | Create secure branded payment links, track lifecycle |
| Invoicing — Create & Lifecycle | Digital Acceptance | ✅ | Generate payment-enabled invoices, track status |
| Terminal Integration (CP) | Card Present | ✅ | Connect POS terminals, manage device fleet, contactless |
| Virtual Terminal | Manual Entry | ✅ | Manual card number entry for MOTO transactions |
| Subscription Management | Recurring Billing | ✅ | Create, update, pause, cancel billing schedules with retry logic |
| Token Create/Retrieve & Network Tokens | TMS | ✅ | Tokenise credentials, Visa Token Service integration |
| FME (Fraud Management Essentials) | Risk | ✅ | Rule-based screening, velocity checks (SMB default) |
| Decision Manager (DM) | Risk | Optional | Advanced ML scoring, custom risk models, Payer Auth orchestration (Enterprise) |
| Payer Authentication (3DS2) | Risk | Optional | SCA compliance, risk-based exemptions — via FME (SMB) or DM (Enterprise) |
| Reporting & Transaction Search API | Analytics | ✅ | Settlement, transaction, dispute reports + query/filter/export |
| Multi-Currency Pricing | Global | Optional | Display and settle in local currencies for cross-border retail |
| Account Updater | Lifecycle | Optional | Auto-refresh expired/reissued cards to reduce payment failures |
| Webhook Notifications | Integration | Optional | Real-time event streaming for payment lifecycle |

---

## Insights

### Partner Needs

- Platform choice guidance — ANET on VAP for SMB (fast, bundled), Enterprise VAP for complex multi-market (flexible, granular)
- Multi-merchant portfolio management with centralized reporting and settlement
- White-label payment UX — partner-branded checkout, receipts, and merchant portal
- Unified token vault across in-store and online for true omni-channel
- Both FME (SMB) and DM (Enterprise) fraud options available depending on complexity needs

### Global Considerations

#### Europe
PSD2/SCA required — 3DS2 exemptions (low-value, TRA, MIT) critical for conversion. SEPA Direct Debit, iDEAL (NL), Bancontact (BE), Klarna (Nordics) expected alongside card. GDPR-compliant data handling. 95%+ contactless adoption in UK, NL, Nordics — CP must be contactless-first.

#### Asia-Pacific
WeChat Pay, Alipay, GrabPay, PayNow critical for conversion. QR-code flows for in-store alongside NFC contactless. Higher mobile commerce penetration requires mobile-optimised checkout. Multi-currency and local acquirer routing for regional chains.

#### Latin America
Parcelas/cuotas are table stakes — issuer and merchant-funded installments required. PIX (Brazil), PSE (Colombia), OXXO (Mexico) as alternative payment methods. Local acquirer routing improves auth rates. Tax document requirements vary (CPF in Brazil, RFC in Mexico).

#### Middle East & Africa
Lower card penetration, growing contactless. mada network required for Saudi Arabia domestic acceptance. Multi-currency essential for UAE expat consumer base. Cash-on-delivery hybrid flows still relevant in some markets.

### Regulatory Notes
PCI DSS Level 1 for partner; SAQ-A eligible for merchants using Unified Checkout (hosted). SCA/3DS2 required in EEA — FME handles for SMB, DM orchestrates for Enterprise. Data residency agreements needed for multi-region. Network Tokens (VTS) improve auth rates and meet scheme mandates.

### Partner Flexibility
Partner must retain ability to curate payment method mix per merchant segment, set individual merchant fee structures, and toggle value-added services on/off per merchant without re-integration. White-label everything. Both platform modules selectable per merchant segment.

### Merchant Segment Variance
SMB retail merchants get turnkey hosted checkout with full product bundle pre-contracted (ANET on VAP, 6–8 weeks). Enterprise retail chains get embedded checkout with custom branding, multi-location settlement splits, DM fraud, and multi-currency (Enterprise VAP, 8–12 weeks).

---

## Integration Path

| Step | Title | Description |
|------|-------|-------------|
| 1 | Sandbox Access | Register on developer portal, obtain sandbox API keys. Configure test merchant profiles with SMB product bundle or Enterprise product selection enabled. |
| 2 | Payment Method Configuration | Enable CP (terminal), CNP (Unified Checkout), Virtual Terminal, Pay By Link, and Invoicing per merchant needs. Configure digital wallet acceptance. |
| 3 | Checkout Integration | Implement Unified Checkout (Flex Microform) for online, terminal integration for in-store. Set up PBL and Invoicing flows. |
| 4 | Merchant Onboarding | Build or use pre-built onboarding flow — KYC, bank account verification, product selection within contracted bundle. |
| 5 | Testing & Certification | Execute test scenarios across all channels (CP, CNP, VT, PBL, Invoice, Recurring). Validate FME/DM rules. PCI compliance. |
| 6 | Go-Live & Scale | Launch with pilot merchants. Monitor via Reporting/Transaction Search. Roll out across portfolio. |

---

[← Back to All Recipes](./index.md)
