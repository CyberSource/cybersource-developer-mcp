---
vertical: Real Estate
description: Rent collection, deposits, and recurring payments for property management and real estate platforms.
module: SMB
integration_model: API
channels: [CNP]
keywords: [real estate, property, rent, lease, landlord, tenant, property management, deposit, hoa]
required_products: [accept-payments, recurring-billing, echeck, digital-invoicing, tms]
---
# 🏠 Real Estate

> Enable partners building rent collection, property management, and real estate transaction platforms — supporting high-value payments, recurring rent, and escrow-adjacent workflows.

| Field | Value |
|-------|-------|
| Recommended Module | SMB |
| Integration Model | API |
| Channels | CNP |

---

## Overview

### Required Products

- Accept Payments
- eCheck
- Digital Invoicing
- Recurring Billing
- Pay By Link

### Typical Use Cases

1. Property management SaaS enables 500+ management companies to collect rent from 50,000+ units with automated disbursement to property owners
2. Tenant portal integrates with property management system — tenants pay rent, submit maintenance requests, and manage autopay
3. Real estate transaction platform facilitates earnest money deposits and closing cost payments with escrow-adjacent fund holding

---

## APIs

### Common APIs (All Recipes)

| API | Category | Required | Description |
|-----|----------|----------|-------------|
| Payment Authorization | Core Payments | ✅ | Authorize transactions across supported channels and payment types |
| Refund & Void | Core Payments | ✅ | Process refunds, void pending authorizations, and handle payment reversals |

### Real Estate APIs

| API | Category | Required | Description |
|-----|----------|----------|-------------|
| eCheck / ACH | Payment Methods | ✅ | Bank transfers for high-value rent and property payments exceeding card limits |
| Recurring Billing | Subscription | ✅ | Automated monthly rent collection with configurable due dates and late fee logic |
| Digital Invoicing | Billing | ✅ | Generate rent statements, maintenance invoices, and property fee notices with embedded payment |
| Pay By Link | Payment Methods | Optional | Payment links for one-time charges — application fees, maintenance bills, move-in costs |
| Webhook Notifications | Integration | Optional | Payment status callbacks for property management system integration and tenant notifications |

---

## Insights

### Global Considerations

#### Europe
Rent payment methods vary dramatically — SEPA Direct Debit dominant in Germany/Netherlands, standing orders in UK, card-based in Southern Europe. Tenant protection regulations impact payment timing and deposit handling. GDPR for tenant payment data.

#### Asia-Pacific
Property payment digitization accelerating — Singapore, Australia, Hong Kong leading. India's RERA regulations create transparency requirements for real estate payments. Build-to-rent growing in Japan/Australia with institutional payment needs.

#### Latin America
Boleto and bank transfer dominant for rent in Brazil. High informality in rental markets — digital payment platforms drive formalization. Currency-indexed leases common in Argentina. Real estate investment trust (FIBRA) structures in Mexico.

#### Middle East & Africa
Post-dated cheque replacement with digital rent collection in UAE (now mandated). Ejari-integrated payments in Dubai. Saudi RERA requirements. Multi-currency for expat tenant populations.

### Regulatory Notes
Security deposit regulations vary by jurisdiction (interest requirements, return timelines, segregated accounts). Tenant payment data protection under GDPR/local privacy laws. Anti-money laundering requirements for high-value real estate transactions. Escrow licensing requirements in many markets.

### Merchant Segment Variance
SMB landlords (1-10 units) need simple rent collection with autopay setup. Enterprise property management companies need multi-property portfolio management, owner reporting, trust accounting integration, and maintenance payment workflows across thousands of units.

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
