# Meridian — AI-Powered Healthcare Quality & ISO Auditing Platform

![Apollo Federation](https://img.shields.io/badge/Apollo-Federation_v2.7-311C87) ![GraphQL](https://img.shields.io/badge/GraphQL-Supergraph-E10098) ![MCP](https://img.shields.io/badge/AI-MCP_agents-7C3AED) ![TypeScript](https://img.shields.io/badge/TypeScript-Node.js-3178C6) ![status](https://img.shields.io/badge/status-architecture_%2F_blueprint-blue)

> A platform unifying international ISO healthcare standards (13485, 14971, 27799, 7101) with Portuguese national quality seals (Selo da Humanização, Selo da Qualidade em Saúde) into one AI-powered, three-sided marketplace connecting providers, certified auditors, and patients — starting in Portugal, designed for the EU.

> **What this repository is:** the **product and technical architecture** for Meridian (blueprint stage) — the GraphQL federation model, the AI/agent layer, the identity and security design, and the full feature scope. It documents the system; the implementation is planned in phases.

## The Three-Sided Marketplace

- **Providers** — a unified dashboard for every certification (ISO + national seals), AI gap analysis, document control, and audit readiness.
- **Auditors** — a specialized marketplace with assessment tooling, finding/CAPA management, client matching, and reputation tracking.
- **Patients** — transparent discovery of quality-certified providers with verified seals, ratings, and safety information.

## AI Intelligence Layer

The defining capability. A dedicated `ai-intelligence-service` subgraph plus the **Apollo MCP Server**, which exposes the platform GraphQL operations as **MCP tools** — so LLM agents can query and orchestrate the system through a standard interface. On top of it:

- Automated document review and **gap analysis** against each standard.
- Compliance-assistant chatbot with standards interpretation (Portuguese / English).
- Humanization scoring, risk forecasting, and predictive compliance-drift warnings.
- Smart recommendations engine for prioritized, resource-aware action items.

## Architecture — Apollo GraphQL Federation v2

A multi-tenant, domain-driven federation orchestrated by an Apollo Router, with one subgraph per domain:
               Apollo Router (Federation Gateway)
                             |
+----------+----------+----------+----------+----------+
healthcare-  portuguese- auditor-   patient-   analytics
iso          seals       marketplace portal     +
+----------+----------+----------+----------+----------+
auth       notification  document   ai-intelligence

**Subgraphs:** healthcare-iso, portuguese-seals, auditor-marketplace, patient-portal, analytics, auth, notification, document, ai-intelligence.

**Architectural principles:** domain-driven design, event sourcing (audit trail and compliance history), CQRS, saga pattern for distributed transactions, circuit breakers, and bulkhead isolation for fault tolerance.

## Identity & Security

| Tier | Provider |
|---|---|
| Patients / providers / auditors | Auth0 (SSO, MFA, passwordless) |
| Enterprise providers / hospitals | Okta (SAML, SCIM, lifecycle) |
| Admin portal / internal | Keycloak (RBAC, self-hosted) |
| Secrets | HashiCorp Vault |

GDPR plus healthcare-data-specific protection throughout.

## Standards & Seals

ISO 13485 (medical-device QMS) · ISO 14971 (risk management) · ISO 27799 (health informatics security) · ISO 7101 (healthcare quality) · Joint Commission International readiness · Selo da Humanização · Selo da Qualidade em Saúde · Selo de Boas Práticas

## Core Features

Multi-standard compliance dashboard with real-time scoring · version-controlled document control with approval workflows, digital signatures, and audit trails · continuous auditing (scheduled and event-triggered checks, deviation detection, certification/calibration tracking) · AI document review and gap analysis · internal-audit tooling with finding and CAPA management · pre-audit gap analysis and documentation packaging.

## Tech Stack

| Layer | Technology |
|---|---|
| Orchestration | Apollo Router v1.35+ · Gateway v2.5+ · Federation v2.7+ · Studio |
| Backend | TypeScript · Node.js subgraphs |
| Frontend | Next.js · React Native |
| Data | PostgreSQL (per subgraph) · MongoDB (documents) · Pinecone/Weaviate (AI vectors) |
| Identity | Auth0 · Okta · Keycloak · HashiCorp Vault |
| AI | Apollo MCP Server · LLM gap analysis, review, and assistant |
| Infra | Kubernetes (multi-cloud) · GitHub Actions |

## Regulatory Positioning

Meridian is a quality **preparation and facilitation** platform. It does not issue official certifications; final approval is handled by accredited certification bodies, with verification partnerships intended with the Direção-Geral da Saúde (DGS) and ACSS.

## Status & Roadmap

Architecture and blueprint stage. Planned MVP focuses on the highest-value combination first: ISO 7101 + Selo da Humanização + a public provider directory, with the auditor marketplace and continuous-auditing engine following.

## Disclaimer

Concept / portfolio artifact. Not affiliated with ISO, the Joint Commission, DGS, or ACSS. Standard and seal names are referenced descriptively.
