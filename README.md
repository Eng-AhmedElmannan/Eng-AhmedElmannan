<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:1e3a5f,100:6366f1&height=160&section=header&text=Ahmed%20Ata%20Elmannan&fontSize=36&fontColor=ffffff&fontAlignY=45&desc=Enterprise%20Architect%20%E2%80%94%20Circle%20AI%20Founder%20%E2%80%94%20Riyadh%2C%20KSA&descSize=16&descAlignY=68&descColor=c7d2fe" width="100%" alt="header"/>

**Enterprise Software Architect · Circle AI Founder · EVP Technology**  
*Multi-Tenant SaaS · Arabic-first Compliance Systems · AI-Augmented Platforms*

[![Location](https://img.shields.io/badge/📍-Riyadh%2C%20Saudi%20Arabia-1e3a5f?style=flat-square)](https://github.com/Eng-AhmedElmannan)
[![Focus](https://img.shields.io/badge/Focus-Enterprise%20SaaS%20%7C%20KSA%20Compliance-6366f1?style=flat-square)](https://github.com/Eng-AhmedElmannan)
[![AI](https://img.shields.io/badge/AI-Custom%20AI%20%7C%20pgvector%20RAG-10b981?style=flat-square)](https://github.com/Eng-AhmedElmannan)
[![Vision](https://img.shields.io/badge/Vision-Saudi%20Vision%202030-dc2626?style=flat-square)](https://github.com/Eng-AhmedElmannan)

[![Circle AI](https://img.shields.io/badge/circleai.sa-000000?style=flat-square)](https://circleai.sa)
[![CircleLaw](https://img.shields.io/badge/law.circleai.sa-Live-000000?style=flat-square)](https://law.circleai.sa)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/ahmed-ata-elmannan-8a11a9238)

</div>

---

## About

I architect and ship enterprise-grade multi-tenant SaaS platforms for the Saudi and Gulf market — alone.

Every platform I build is designed for compliance from day one: cryptographic tenant isolation, regulatory integration (ZATCA Phase 2, PDPL, MOJ court taxonomy), AI-augmented workflows, and immutable production governance. The platforms under this profile are not prototypes. They carry production workloads for law firms operating in an environment where uptime, data integrity, and regulatory compliance are non-negotiable.

> *Design for isolation first. Compose second. Scale third.*

---

## The Circle AI Ecosystem

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        C I R C L E  A I                                 │
│                  Enterprise Platform Suite · circleai.sa                │
├──────────────────┬──────────────────────┬──────────────────────────────┤
│   CircleLaw      │    CircleCRM         │    CircleSpend               │
│   ─────────────  │    ──────────────    │    ──────────────────────    │
│   Enterprise     │    Multi-Tenant      │    Employee Spend            │
│   Legal Practice │    CRM Platform      │    Management &              │
│   Management     │    Leads · Projects  │    Policy Engine             │
│                  │    Invoices · CX     │                              │
│   ✓ LIVE v2.22   │    ◎ In Development  │    ◎ In Development          │
├──────────────────┴──────────────────────┴──────────────────────────────┤
│                    SHARED PLATFORM LAYER                                │
│   DB-per-Tenant Engine · RBAC/MFA · Audit Log · Subscription Billing   │
│   Django 5 · PostgreSQL 15 + pgvector · Redis 7 · Celery · PgBouncer  │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## CircleLaw — Flagship `[LIVE · v2.22.3]`

> Enterprise legal-practice management for KSA/MENA law firms · [law.circleai.sa](https://law.circleai.sa)

| Capability | Detail |
|---|---|
| **Multi-tenancy** | Separate PostgreSQL database per tenant · custom ORM router with `.using(alias)` discipline · 13-gate structural validation before activation |
| **ZATCA Phase 2** | Full end-to-end: UBL 2.1 XML · XAdES-BES cryptographic signing · Schematron/XSLT 2.0 (Saxon) validation · 9-tag TLV QR encoding · FATOORA clearance/reporting with retry |
| **AI & Legal Workflows** | Custom AI model: pleading drafts · consultation RAG over local pgvector + sentence-transformers · meeting-notes extraction · PII redaction on output (PDPL-compliant — data stays within tenant boundary) |
| **Field Encryption** | Fernet for opaque PII fields · AES-SIV deterministic for equality-searchable fields (email, NID) |
| **Court Integration** | 160+ Saudi courts, cities, and jurisdictions — MOJ-aligned taxonomy · Hijri + Gregorian dual-calendar with automated deadline enforcement |
| **Billing & Dunning** | Per-tenant plans · feature gating · staged dunning ladder (grace → read-only → locked → suspended) · Redis-versioned cache with fail-closed defaults |
| **Security** | TOTP + Email OTP MFA · Lua atomic Redis challenge commit/verify · context fingerprinting · RBAC across 4 access tiers · brute-force lockout |
| **Release Governance** | `develop → PR → main → annotated tag → VPS` only · weekly automated pipeline · zero production hotfixes · full traceability: tag → PR → CI → deploy event |

```
~1,857 commits · v2.22.3 (prod v2.21.2) · 81 models · 70+ API resources · 200+ REST routes
347 migrations · solo-authored · hardened self-hosted deployment · live in production
```

**Stack:** `Django 5` `DRF` `Celery` `Vue 3` `Vite` `Pinia` `TypeScript` `Astro 4` `PostgreSQL 15` `pgvector` `PgBouncer` `Redis 7` `Docker` `Caddy`

---

## Circle AI Platform Suite

*The CircleLaw multi-tenant engine, productized into adjacent verticals — one architecture, multiple domains:*

**CircleCRM** — Generic multi-tenant CRM (leads, clients, projects, tasks, invoices, estimates, support tickets).  
Full enterprise trait inheritance from CircleLaw: DB-per-tenant isolation · field-level PII encryption · GlobalAuditLog taxonomy · Stripe billing with webhook idempotency · MS Graph email backend · RBAC + MFA.

**CircleSpend** *(in active development)* — Employee spend management platform.  
Declarative spend-policy engine: evaluates expenses against limit/approval-rule DSL, deterministic approval routing by amount and cost center. Budget burn-rate tracking with threshold alerts · AI-powered receipt-OCR enrichment · local pgvector similarity for receipt and client deduplication.

> These share the CircleLaw platform architecture — vertical productization on a proven multi-tenant chassis, not independent rewrites. The architecture is the asset.

---

## circleai.sa — Corporate Site

> `Next.js 16` `React 19` `Tailwind 4` `shadcn/ui` · [circleai.sa](https://circleai.sa) · 14 tagged releases (v0.3.1)

Production bilingual EN + Arabic RTL, locale-persisted across sessions. Tag-triggered CI/CD · Docker multi-stage non-root builds · health-check gate (12×5s) · **auto-rollback to previous image digest on failure** · hardened reverse-proxy headers.

---

## Engineering Highlights

- **ZATCA Phase-2 end-to-end** — UBL 2.1, XAdES-BES cryptographic signing, Schematron/XSLT 2.0 validation, 9-tag TLV QR, FATOORA submission with retry. One of few engineers to have shipped this complete stack in a live product.
- **RAG inside a regulated SaaS** — Local pgvector inference on a running Django platform, PII-redacted before any data reaches the AI model. PDPL-compliant by design, not by policy.
- **True database-per-tenant isolation** — Not schema-level, not row-level: a dedicated PostgreSQL database per tenant, enforced at the ORM router with 13 structural validation gates before activation.
- **Dual-scheme field encryption** — Fernet for opaque PII, AES-SIV deterministic for equality-searchable fields. Two schemes because the access patterns are fundamentally different.
- **Solo, shipped, maintained** — One engineer. Every design decision, migration, deployment, and production incident. 2+ years. Live B2B SaaS.

---

## Platform Architecture Philosophy

**Isolation is a first-order constraint.**  
Tenant isolation is not a layer added to a single-tenant system. It is the structural premise that determines every database schema, every ORM query, and every permission check. It cannot be retrofitted — it must be the premise.

**Security is defined before the first migration is written.**  
MFA, encryption design, and audit trail structure are architectural decisions, not features added post-launch. The CircleLaw MFA system — TOTP + Email OTP, Redis-backed Lua atomic challenge store, context fingerprinting — was specified as a security constraint before any application code was written.

**Governance is not overhead — it is the product.**  
An immutable deployment pipeline, audit-logged releases, and a prohibition on VPS hotfixes are not bureaucracy. They are the mechanism by which a system remains trustworthy across years of change. Every CircleLaw production release is traceable to a git tag, a PR, a CI run, and a deploy event. That traceability is the architecture.

**Architecture is a long-term bet.**  
Every technical decision is evaluated against a 5-year maintenance cost, not a 5-week delivery timeline. Premature abstraction and feature-driven complexity are more expensive than the problems they were supposed to solve.

**AI augments. It does not replace.**  
In legal, HR, and financial domains, AI is a decision-support instrument. Autonomous AI action in any domain that produces a legal record, a disbursement, or a financial entry is an architectural anti-pattern. Human confirmation is a system requirement, not an option.

---

## Saudi & Gulf Market Focus

The Circle AI platforms are architected for the regulatory and cultural context of Saudi Arabia and the GCC:

- **Arabic-first UX** — RTL layout, Arabic error messages, Hijri + Gregorian dual-calendar with automated deadline enforcement
- **ZATCA Phase 2** — Full e-invoicing compliance with cryptographic signing (XAdES-BES) and FATOORA integration, live in production
- **PDPL Architecture** — Saudi Personal Data Protection Law controls at the infrastructure level; AI inference runs locally within tenant boundary, data never leaves
- **Saudi Legal Context** — 160+ court jurisdictions aligned to MOJ taxonomy; Wakalah, appeal windows, and Saudi court procedure modelled at the domain layer
- **Vision 2030** — Locally-built, sovereign-grade enterprise platforms replacing imported software in Saudi legal and enterprise markets

---

## AI Integration Layers

**Layer 1 — Operational Intelligence (CircleLaw · Live)**  
Consultation RAG over local pgvector embeddings, pleading generation, legal document drafting, meeting-notes extraction — via a custom proprietary AI model. PII is redacted before leaving the tenant compute boundary. PDPL-compliant by architecture.

**Layer 2 — Operational Enrichment (CircleSpend · In Development)**  
AI-powered receipt OCR enrichment, local pgvector similarity for receipt and client deduplication. Spend-policy evaluation is deterministic — AI enriches input, policy enforces output.

**Layer 3 — Platform Intelligence (Planned)**  
Provider-agnostic inference interface attaching to any CircleAI platform through a stable internal API contract. Supports proprietary, open-source, and self-hosted models. Federated architecture — tenant data never crosses its isolation boundary.

---

## Roadmap

| Horizon | Initiative | Status |
|---|---|---|
| **Now** | CircleLaw v2.x — Production-hardened, active feature development | ✅ Live |
| **Now** | CircleCRM — Multi-tenant CRM platform productization | 🔨 Active |
| **Q3 2026** | CircleSpend — Spend management, policy engine, budget tracking | 🔨 Active |
| **Q4 2026** | CircleHR — HR & payroll platform, Qiwa / GOSI / WPS integration | 📋 Planned |
| **2027** | CircleFinance — CFO intelligence, cash-flow AI, GL automation | 📋 Planned |
| **2027** | CircleAI Unified — Cross-platform intelligence, federated analytics, SSO | 🔭 Vision |
| **2027+** | Gulf Regional Expansion — UAE, Kuwait, Bahrain | 🔭 Vision |

---

## Enterprise Collaboration

I engage with organisations seeking to:

- Architect or audit enterprise SaaS platforms for the Saudi and Gulf market
- Accelerate Vision 2030 digital transformation initiatives
- Evaluate or adopt CircleLaw, CircleCRM, or CircleSpend
- Establish technical partnerships in the enterprise software space

> For enterprise inquiries, architecture consultations, or partnership discussions — connect via LinkedIn or through the repositories.

<div align="center">

**[circleai.sa](https://circleai.sa) · [law.circleai.sa](https://law.circleai.sa) · [LinkedIn](https://linkedin.com/in/ahmed-ata-elmannan-8a11a9238)**

---

*Circle AI — Engineering enterprise-grade software for the Saudi market.*

[![GitHub](https://img.shields.io/badge/GitHub-Eng--AhmedElmannan-181717?style=for-the-badge&logo=github)](https://github.com/Eng-AhmedElmannan)

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:6366f1,100:1e3a5f&height=80&section=footer" width="100%"/>

</div>
