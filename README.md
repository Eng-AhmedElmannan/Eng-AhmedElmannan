<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:1e3a5f,100:6366f1&height=160&section=header&text=Ahmed%20Ata%20Elmannan&fontSize=36&fontColor=ffffff&fontAlignY=45&desc=EVP%20of%20Technology%20%E2%80%94%20CircleAI%20Ecosystem&descSize=16&descAlignY=68&descColor=c7d2fe" width="100%" alt="header"/>

**Executive Vice President of Technology**
*Enterprise Software Architecture · Cloud-Native SaaS · AI Systems Design*

[![Location](https://img.shields.io/badge/📍-Saudi%20Arabia%20%7C%20Gulf%20Region-1e3a5f?style=flat-square)](https://github.com/Eng-AhmedElmannan)
[![Focus](https://img.shields.io/badge/Focus-Enterprise%20SaaS%20%7C%20Multi--Tenant%20Platforms-6366f1?style=flat-square)](https://github.com/Eng-AhmedElmannan)
[![Security](https://img.shields.io/badge/Security-MFA%20%7C%20Encrypted%20Vault%20%7C%20Audit%20Log-10b981?style=flat-square)](https://github.com/Eng-AhmedElmannan)
[![Vision](https://img.shields.io/badge/Vision-Saudi%20Vision%202030-dc2626?style=flat-square)](https://github.com/Eng-AhmedElmannan)

</div>

---

## Executive Introduction

I lead platform architecture and product strategy for the **CircleAI** ecosystem — a suite of
enterprise-grade, multi-tenant SaaS platforms purpose-built for the Saudi and Gulf markets.

My work sits at the intersection of distributed systems design, enterprise security architecture,
and AI-augmented product strategy. Every platform I build is designed to operate at compliance
grade from day one: SOC 2-aligned audit trails, cryptographic tenant isolation, multi-factor
authentication, zero-trust permission models, and container-native infrastructure with full
production observability.

The platforms I architect are not prototypes. They carry production workloads for law firms,
enterprises, and public-sector entities — environments where uptime, data integrity, and regulatory
compliance are non-negotiable.

---

## The CircleAI Ecosystem

**CircleAI** is a unified intelligent enterprise platform composed of three specialized verticals,
each independently deployable and jointly composable through a shared infrastructure layer.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        C I R C L E  A I                                 │
│              Unified Intelligent Enterprise Platform                    │
├──────────────────┬──────────────────────┬──────────────────────────────┤
│   CircleLAW      │    CircleHR          │    CircleFinance             │
│   ─────────────  │    ──────────────    │    ──────────────────────    │
│   Enterprise     │    Intelligent       │    Smart Financial           │
│   Legal Practice │    Human Capital &   │    Operations &              │
│   Management     │    Payroll Platform  │    Cost Intelligence         │
│                  │                      │                              │
│   ✓ LIVE v1.10   │    ◎ In Development  │    ◎ In Development          │
├──────────────────┴──────────────────────┴──────────────────────────────┤
│                    SHARED PLATFORM LAYER                                │
│   Multi-Tenant Engine · RBAC/RLS · MFA · Audit Trails · Billing Engine │
│   Docker Compose · PostgreSQL 15 Clusters · Redis 7 · Celery · PgBouncer│
└─────────────────────────────────────────────────────────────────────────┘
```

---

## CircleLAW — Enterprise Legal Practice Management `[LIVE · v1.29.0]`

Full-lifecycle legal practice management platform for Saudi law firms and corporate legal
departments. Production-hardened across 10+ versioned releases with an immutable deployment
governance model.

### Platform Capabilities

| Capability | Detail |
|---|---|
| Case Lifecycle | End-to-end from intake through judgment, appeal, and enforcement |
| Court Integration | 160+ Saudi courts, cities, and jurisdictions — MOJ-aligned taxonomy |
| Calendar Engine | Hijri + Gregorian dual-calendar with automated deadline enforcement |
| Document Engine | OCR pipeline (Arabic + English), template management, digital signatures |
| Permission Depth | 18+ granular RBAC permissions across 4 access tiers |
| MFA Security | TOTP + Email OTP with Redis-backed challenge store and context fingerprinting |
| Compliance | Structured audit log retention, row-level tenant isolation, encrypted vault |
| API Surface | 200+ REST endpoints — OpenAPI/Swagger documented |
| Client Portal | Dedicated read-only portal for client case and invoice access |

### Technical Stack

| Layer | Technology |
|---|---|
| Backend | Django 5 + Django REST Framework + Celery + Celery Beat |
| Frontend | Vue 3 (Composition API) + Vite + TailwindCSS v3 |
| Database | PostgreSQL 15 — database-per-tenant architecture |
| Connection Pooler | PgBouncer (transaction mode, port 6432) |
| Cache / Broker | Redis 7 |
| Authentication | JWT sessions + TOTP/Email MFA (Redis challenge store, HMAC-verified OTP) |
| Deployment | Docker Compose — self-hosted VPS, Ubuntu |
| CI/CD | GitHub Actions — semver-tagged immutable releases |
| Reverse Proxy | Caddy (automatic HTTPS, HTTP/2) |

### Production Maturity Indicators

```
Release cadence   →  v1.0 → v1.10.5 — 10+ production releases
Deployment model  →  Immutable: semver tags → GitHub Actions → VPS checkout
Governance        →  No direct commits to main · No hotfixes on VPS · Full audit trail
Security posture  →  MFA · Encrypted field vault · Brute-force lockout · CSRF · CSP
Database scale    →  149-table core schema + 128-135 tables per tenant DB
API surface       →  200+ REST endpoints, fully documented
Migration safety  →  Atomic migrations · Alias guards · Cross-DB contamination blocked
```

---

## Platform Architecture Philosophy

> *"Design for isolation first. Compose second. Scale third."*

Every platform in the CircleAI ecosystem follows five non-negotiable architectural principles:

**1. Tenant Isolation at the Database Layer**
Each customer operates on a dedicated PostgreSQL database with no shared table space.
PgBouncer (transaction mode) provides connection pooling without compromising isolation.
Cross-database foreign keys are explicitly prohibited; reference data is routed via a
purpose-built DB router to the global core database.

**2. Security as a First-Class Design Constraint**
Zero-trust is not a feature added post-launch. MFA is implemented at the authentication
layer with provider-agnostic architecture (TOTP and Email OTP supported simultaneously).
Permission enforcement runs at three independent layers: database routing, API viewset
policy, and frontend route guards. Every privileged action is audited.

**3. Upgrade-Safe Modularity**
Platform modules are structured so that any component can be disabled, upgraded, or replaced
without side-effects on neighbouring modules. Migrations are atomic, reversible, and protected
by alias guards to prevent cross-database contamination.

**4. Observability by Default**
Structured logging, health endpoints, and container-level monitoring are wired at the framework
level — not bolted on. Health endpoints expose dependency status (DB, cache, celery) without
leaking internal topology. Production deploys are gated on health check passage.

**5. AI-Readiness Without Vendor Lock-in**
Platform data models are normalised for AI workload ingestion. Inference endpoints,
embedding pipelines, and LLM orchestration layers can attach to any CircleAI platform
through a stable internal API contract — provider-agnostic by design.

---

## Security & Compliance Architecture

```
Authentication Layer
  └── JWT sessions with configurable expiry
  └── MFA: TOTP (authenticator apps) + Email OTP (Celery-delivered)
  └── Redis-backed challenge store: HMAC-verified OTP, Lua atomic commit/verify
  └── Context fingerprinting: UA + subnet + tenant hash — logs anomalies
  └── Brute-force lockout · Password strength enforcement · Account lockout audit

Authorization Layer
  └── RBAC: Role → Permission (module.action) · 3-level access: view / partial / full
  └── 4 access tiers: Owner, Admin, Staff, Client Portal
  └── RLS: Tenant DB isolation · Row-filtered queries · Admin bypass with audit log
  └── 18+ granular permissions — case-level, document-level, invoice-level

Data Protection Layer
  └── Fernet encryption (client vault) · AES field-level encryption
  └── Row-level change audit · Global audit log (platform operations)
  └── FIELD_ENCRYPTION_KEY + SECRET_KEY: immutable per environment, vault-managed
  └── Automated daily PostgreSQL backups · Configurable retention

Transport & Infrastructure Layer
  └── HTTPS enforced (HSTS, SECURE_SSL_REDIRECT via Caddy) · CSRF protection
  └── CSP headers · Rate limiting (per-user + per-IP) · Sanitized error responses
  └── No port 8000 host-mapped — all external traffic through Caddy 80/443
  └── PgBouncer: DB credentials never exposed to application layer directly

Compliance Posture
  └── SOC2 Type II aligned architecture
  └── PDPL (Saudi Personal Data Protection Law) controls
  └── Structured audit retention · Zero-knowledge tenant isolation
  └── Full deployment audit trail via immutable git tags + GitHub Actions logs
```

---

## Immutable Deployment Governance

CircleLAW operates under a production governance model designed for auditability,
determinism, and reversibility:

```
LOCAL DEVELOPMENT
─────────────────
  Develop on feature branches → commit to develop → push to GitHub

        │
        ▼  GitHub Actions CI gates
        │
PULL REQUEST  (develop → main)
──────────────────────────────
  Docker build validation · Security scan · Migration check
  No PR merges with failing required CI gates

        │
        ▼  main is now at validated commit
        │
RELEASE TAG  (annotated semver, on main)
────────────────────────────────────────
  git tag -a v1.10.5 -m "Release v1.10.5: ..."
  git push origin v1.10.5

        │
        ▼  GitHub Actions deployment workflow triggered
        │
VPS DEPLOYMENT  (automated, immutable)
───────────────────────────────────────
  git fetch --tags
  git checkout v1.10.5          ← detached HEAD — always pinned to tag
  docker compose -f docker-compose.prod.yml up -d --build
  manage.py migrate --noinput
  health check → confirmed

        │
        ▼
POST-DEPLOY SYNC
────────────────
  develop synced to main immediately after every merge
```

**Governance constraints (absolute, no exceptions):**
- `main` advances only via PR merge — never direct commits
- VPS always runs a detached HEAD at a version tag — never a branch
- `git pull` is permanently prohibited on VPS
- All fixes — including critical security patches — travel the full pipeline
- No files edited directly on VPS filesystem (configuration drift = governance violation)

---

## Multi-Tenant Architecture

The CircleAI platforms implement **database-per-tenant** isolation — the most robust
multi-tenancy model for enterprise workloads.

```
Platform Request Lifecycle
─────────────────────────
HTTP Request
    │
    ├─► Platform Auth Middleware   (validates JWT, MFA status)
    │
    ├─► Tenant Resolution          (slug → DB alias lookup from circlelaw_core)
    │
    ├─► DB Router Activation       (routes ORM to tenant DB)
    │
    ├─► PgBouncer (port 6432)      (transaction-mode pooling — auth_type=any)
    │
    ├─► Tenant PostgreSQL DB       (fully isolated schema — 128-135 tables)
    │       ├── Cases, Clients, Invoices, Staff, Documents...
    │       └── No shared tables with any other tenant
    │
    └─► Response (tenant-scoped, RLS-filtered)

Database Topology
──────────────────
PostgreSQL 15 instance
  ├── circlelaw          ← default Django DB (149 tables)
  ├── circlelaw_core     ← platform core: tenants, billing, users (26 tables)
  └── circlelaw_tenant_* ← one DB per tenant (128-135 tables each)

Reference data (courts, jurisdictions, currencies) routes via DB router
to circlelaw_core — never stored per-tenant, never cross-DB foreign keys.
```

**Subscription Lifecycle Management**
Each tenant subscription follows canonical lifecycle states:
`trial → active → grace → read_only → locked → cancelled`
Dunning progression is automated. Billing cycle drives permission enforcement in real time.

---

## AI Integration Strategy

The CircleAI platforms are engineered with three AI integration layers:

**Layer 1 — Operational Intelligence (CircleLAW, live)**
Pattern recognition on case timelines, deadline risk scoring based on historical hearing data,
and automated document classification using the existing OCR pipeline. Deterministic
rule-based AI primitives — no external API dependency.

**Layer 2 — Generative Augmentation (CircleHR, in development)**
LLM-backed HR Copilot for natural-language policy retrieval, contract clause explanation,
and onboarding workflow guidance. Built against a provider-agnostic inference interface
supporting OpenAI, Anthropic, and locally-hosted models.

**Layer 3 — Predictive Analytics Engine (CircleFinance, in development)**
Time-series forecasting for payroll, cash flow, and budget variance. Statistical models
trained on per-tenant historical data — federated architecture ensures tenant data never
leaves its isolated compute boundary.

> **Architecture Constraint**: AI augmentation enhances decision-making. It does not make
> autonomous decisions in legal, payroll, or financial domains. Human confirmation is required
> for any AI-generated output that produces a downstream legal or financial record.

---

## CircleHR — Intelligent Human Capital Platform `[In Development]`

AI-augmented HR and payroll intelligence platform aligned with Saudi regulatory requirements.

| Capability | Detail |
|---|---|
| Compliance Engine | WPS (Wage Protection System), Qiwa, GOSI integration |
| AI Copilot | Context-aware HR assistant for policy queries and workflow guidance |
| Payroll Forecasting | Predictive payroll engine with variance alerts |
| Smart Scheduling | AI-driven shift optimisation and conflict resolution |
| Expense Governance | OCR receipt processing, policy enforcement, GL integration |
| Analytics | Predictive attrition modelling, workforce insights |

---

## CircleFinance — Smart Financial Operations Platform `[In Development]`

AI-driven financial intelligence platform for enterprise CFO visibility and operational control.

| Capability | Detail |
|---|---|
| Financial Intelligence | AI-driven variance analysis and anomaly detection |
| Cash Flow Modelling | Predictive rolling forecasts with scenario simulation |
| Budget Governance | Real-time consumption tracking with threshold alerting |
| GL Automation | Automated journal entries with rule-based posting engine |
| ERP Integration | Standardised integration layer for Odoo, SAP, Oracle |
| CFO Dashboards | Executive KPI visualisation with drill-through capability |
| Multi-Entity | Consolidated reporting across legal entities and cost centres |

---

## Saudi & Gulf Digital Transformation

The CircleAI platforms are architected specifically for the regulatory and cultural context
of Saudi Arabia and the Gulf Cooperation Council:

- **Arabic-first UX** — RTL layout, Cairo typeface, Arabic error messages, Hijri calendar
- **Saudi Legal Compliance** — Court taxonomy aligned to MOJ structure, 160+ jurisdictions
- **Saudi HR Compliance** — WPS, Qiwa, GOSI payroll integration ready
- **PDPL Alignment** — Saudi Personal Data Protection Law architectural controls
- **Vision 2030 Positioning** — Replacing imported enterprise software with locally-built,
  sovereign-grade platforms for Saudi law firms, enterprises, and government entities
- **SAR Native** — Financial calculations, invoicing, and reporting in Saudi Riyals with
  cultural formatting (Arabic numeral conventions, SAR symbol)

---

## Roadmap

| Horizon | Initiative | Status |
|---|---|---|
| **Now** | CircleLAW v1.10 — Production-hardened, active feature development | ✅ Live |
| **Q1–Q2 2026** | CircleHR Alpha — Core HR, payroll engine, Qiwa/GOSI connectors | 🔨 Active |
| **Q2 2026** | CircleHR Beta — AI Copilot, smart scheduling, expense OCR | 📋 Planned |
| **Q2 2026** | CircleFinance Alpha — GL engine, budget governance, CFO dashboard | 📋 Planned |
| **Q3 2026** | CircleAI Platform Layer — Shared identity, unified billing, SSO | 📋 Planned |
| **Q4 2026** | CircleFinance Beta — Cash flow AI, ERP integration, risk scoring | 📋 Planned |
| **2027** | CircleAI Unified — Cross-platform intelligence, federated analytics | 🔭 Vision |
| **2027** | SOC2 Type II Certification — Formal audit engagement | 🔭 Vision |
| **2027+** | Gulf Regional Expansion — UAE, Kuwait, Bahrain market entry | 🔭 Vision |

---

## Leadership Philosophy

**Architecture is a long-term bet.**
Every technical decision I make is evaluated against a 5-year maintenance cost, not a 5-week
delivery timeline. Premature abstraction and feature-driven complexity are more expensive than
the problem they were supposed to solve.

**Security cannot be retrofitted.**
MFA, encryption design, and audit trail structure are defined before the first migration is
written — not during a security review after launch. The CircleLAW MFA system (TOTP + Email
OTP, Redis-backed challenge store, context fingerprinting) was architected as a security freeze,
not a feature addition.

**Multi-tenancy is a first-order constraint.**
Tenant isolation is not a layer added to a single-tenant system. It is the structural premise
that determines every database schema, every ORM query, and every permission check.

**Governance is not overhead — it is the product.**
An immutable deployment pipeline, audit-logged releases, and a prohibition on VPS hotfixes are
not bureaucracy. They are the mechanism by which a system remains trustworthy over years of
change. Every CircleLAW production release is traceable to a git tag, a PR, a CI run, and a
deploy event. That traceability is the architecture.

**AI augments. It does not replace.**
In legal, HR, and financial domains, AI is a decision-support instrument. Autonomous AI action
in any domain that produces a legal record, a payroll disbursement, or a financial entry is an
architectural anti-pattern.

---

## Contact & Enterprise Collaboration

I engage with organisations seeking to:
- Architect or audit enterprise SaaS platforms for the Gulf market
- Accelerate Saudi Vision 2030 digital transformation initiatives
- Evaluate or adopt CircleLAW, CircleHR, or CircleFinance
- Establish technical partnerships in the enterprise software space

> For enterprise inquiries, architecture consultations, or partnership discussions —
> reach out directly via GitHub or through the project repositories.

<div align="center">

---

*CircleAI — Engineering the infrastructure of Saudi enterprise intelligence.*

[![GitHub](https://img.shields.io/badge/GitHub-Eng--AhmedElmannan-181717?style=for-the-badge&logo=github)](https://github.com/Eng-AhmedElmannan)

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:6366f1,100:1e3a5f&height=80&section=footer" width="100%"/>

</div>
