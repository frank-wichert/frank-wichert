<div align="center">

<img src="./assets/avatar.png" alt="Frank Wichert" width="200" />

# Frank Wichert

**Interim Manager · CIO · Projekt- und Krisenmanager · KI-Experte · Keynote Speaker**

*DARC Management UG · Gevelsberg*

[![Web](https://img.shields.io/badge/darc--transform.de-1F2937?style=for-the-badge&logo=googlechrome&logoColor=white)](https://darc-transform.de)
[![DARION](https://img.shields.io/badge/darion--ai.de-2563EB?style=for-the-badge&logo=googlechrome&logoColor=white)](https://darion-ai.de)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/frank-wichert-5b0017294/)
[![Email](https://img.shields.io/badge/frank.wichert%40darc--mgt.de-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:frank.wichert@darc-mgt.de)
[![Verfügbar](https://img.shields.io/badge/48h_einsatzbereit-22C55E?style=for-the-badge)]()

</div>

---

## Über mich

Erfahrener Manager mit **20-jähriger Führungspraxis**, Interim- und Projektmanager mit über **80 Mandaten in 15+ Branchen**. Sparringspartner und Mentor, Keynote Speaker — zielgerichtet, transparent und durchsetzungsstark. Erfahrung im nationalen und internationalen Umfeld (DACH, Spanien, Dubai), in KMU, Konzernen und Familienunternehmen.

Als ehemaliger Soldat auf Zeit (12 Jahre) verbinde ich operative Klarheit mit strategischer Tiefe. Schwerpunkte: **Sanierung, Stabilisierung, Vakanzüberbrückung** sowie **Digitalisierung, AI/KI, Cyber-Security, KRITIS/NIS 2.0** und **M&A für IT**.

<div align="center">

| 80+ | 20+ | 15+ | 120+ |
|:---:|:---:|:---:|:---:|
| **Mandate** | **Jahre Führung** | **Branchen** | **Mitarbeiter als CIO** |

</div>

---

## Aktuelle DARC-Eigenentwicklungen — seit 08/2024

> *Seit Q3 2024 baue ich als Lead Architect mit einem Kernteam (zwei Entwickler plus AI-Pair-Programming) produktive Plattformen und Infrastruktur-Bausteine auf. Eigenentwicklung mit Pilotkunden, Multi-Tenancy als Fundament, IT-Sicherheit und Compliance von Beginn an mitgedacht.*

| # | Projekt | Beschreibung | Status | Tech-Stack |
|---|---------|--------------|--------|------------|
| 1 | **DARION — Multi-Tenant SaaS** | Modulare HR- & Projekt-Management-SaaS mit 18+ Fachmodulen (Leistungserfassung/PSA, Buchhaltung/DATEV, Projekte, Reporting), Multi-LLM-Routing, RAG-Layer, Live-Cockpit, CNPG-HA mit Pooler, CI/CD ≥80 % Coverage | Launch 18.08.2026 | FastAPI · Next.js 15 · K3s · CloudNativePG · Claude API · RAG · OpenTelemetry |
| 2 | **Tina — Autonome KI-Software-Entwicklung** | Orchestrierter Coding-Agent (Temporal-Conductor/L0) mit Plan-/Critic-/Recall-Rollen, Distillations-Lern-Loop, 64k-Coder-Kontext (YaRN), strikter Gewaltenteilung (kein Auto-Merge); Bedienung aus core.darion-ai.de | Produktiv (Core-Hub) | Temporal · Claude · Qwen2.5-Coder · vLLM · Catalyst · MCP |
| 3 | **DARION Core — Agenten-Orchestrierung** | Mixture-of-Agents-Framework mit Plan-, Critic-, Recall-Agent und Orchestrator; Unified Query Hub (6 Routen), Knowledge-Graph, 176 grüne Tests | 6 Phasen produktiv | Claude · LiteLLM · Graphiti · Neo4j · MCP · Langfuse |
| 4 | **Wissens-Architektur & Self-Hosted-Wiki** | Souveräner Knowledge-Hub auf Outline (docs.darion-ai.tech) mit SSO und Federation zum Agenten-Wissensspeicher | Produktiv | Outline · Keycloak · Cloudflare Access · PostgreSQL · MinIO |
| 5 | **KI-Governance — Supporter ⇄ Assistenz** | Hart getrennte interne KI-Rollen nach Least-Privilege (ERP-Supporter ohne Dokumente vs. need-to-know-RAG-Assistenz), durchgesetzt in der DB statt im Prompt, EU-AI-Act-konform | Konzept build-ready | PostgreSQL RLS · JWT · RAG · EU AI Act Art. 50 · Redact-before-Embed |
| 6 | **Identity-, Geheimnis- & Schlüssel-Management** | Dualer Vault-Ansatz mit zweiter Vertrauenslinie, dokumentiertem Schlüssel-Lebenszyklus, Service-Accounts und scoped-Token-Minting | In Betrieb | Vaultwarden · 1Password · OIDC · MFA · TLS · Append-Only |
| 7 | **Server-Cluster mit Mesh-VPN & Tenant-Isolation** | Flotte (5 VPS + 2 Bare-Metal CPU/GPU) mit Mesh-VPN, mehrschichtiger Firewall (DOCKER-USER-Layer), Reverse-Proxy, Cloudflare WAF, einheitlichem Hardening; inkl. Domain-Migration .de → .tech (6 Subdomains) | In Betrieb | Hetzner · Netbird · WireGuard · Cloudflare WAF · K3s · Caddy |
| 8 | **Configuration-Management & Provisionierung** | Zentrales Inventory aller Mesh-Knoten, idempotente Playbooks (Hardening, SSH, Fail2Ban, Backup), Dry-Run-Workflow mit grüner Verifikation | Phase 5 | Ansible · YAML · Jinja2 · Vault-Lookup · Git |
| 9 | **E2EE-Messaging-Migration** | Vollständige Ablösung von Telegram durch self-hosted Matrix mit Cross-Signing, gehärteter Webhook-API mit Themenkanälen, bewusster Federations-Reduktion | Phasen 1–4 fertig | Matrix-Synapse · Element · matrix-nio · Olm/Megolm · Cross-Signing |
| 10 | **Backup-, Monitoring- & Observability-Stack** | Append-Only-Backup mit Restore-Verifikation und Offsite-Kopie; Live-Cockpit (SSE) für Fleet-Health, LLM-Spend, Backup-Status, Heartbeat; node_exporter-Flottenabdeckung | In Betrieb | restic · SFTP · PostgreSQL · OpenTelemetry · Prometheus · SSE |
| 11 | **Job-Discovery- & Lead-Enrichment-Pipeline** | Mehrquellige Pipeline (Apollo, SerpAPI, BA) mit RAG-Sync, Cross-Host-Review-Oberfläche, regelbasierter Auto-Klassifikation (>85 %) plus LLM-Restmenge | In Betrieb | FastAPI · PostgreSQL · Apollo · SerpAPI · BA-API · AnythingLLM |
| 12 | **DARC-Funnel & Marketing-Properties** | Eigenständige Marketing-Sites (darc-transform.de, darion-ai.de/.tech) plus Lead-Funnel mit Selbstcheck-Logik und CRM-Anbindung | Live | Next.js · Hostinger · Cloudflare · Docker Swarm · CRM-Intake |

---

## Tech-Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat&logo=nextdotjs&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![Neo4j](https://img.shields.io/badge/Neo4j-008CC1?style=flat&logo=neo4j&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat&logo=redis&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/K3s-326CE5?style=flat&logo=kubernetes&logoColor=white)
![Hetzner](https://img.shields.io/badge/Hetzner-D50C2D?style=flat&logo=hetzner&logoColor=white)
![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=flat&logo=cloudflare&logoColor=white)
![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=flat&logo=ansible&logoColor=white)
![Claude](https://img.shields.io/badge/Claude_API-CC785C?style=flat&logo=anthropic&logoColor=white)
![Matrix](https://img.shields.io/badge/Matrix-000000?style=flat&logo=matrix&logoColor=white)

---

## IT-Sicherheit & Compliance

> *Querschnitt über alle Projekte — von Beginn an mitgedacht.*

![DSGVO](https://img.shields.io/badge/DSGVO-1F2937?style=for-the-badge)
![EU AI Act](https://img.shields.io/badge/EU_AI_Act_Art._50-1F2937?style=for-the-badge)
![NIS2](https://img.shields.io/badge/NIS_2.0-1F2937?style=for-the-badge)
![ISO 27001](https://img.shields.io/badge/ISO_27001%3A2022-1F2937?style=for-the-badge)
![BSI Grundschutz](https://img.shields.io/badge/BSI_Grundschutz-1F2937?style=for-the-badge)
![BSI C5](https://img.shields.io/badge/BSI_C5%3A2026-1F2937?style=for-the-badge)

**Operative Säulen:** Vault & Schlüssel-Lifecycle · Append-Only-Backup · Mesh-VPN-Default · E2EE-Kommunikation

---

## 🎤 Keynote Speaker

**Aktuelle Keynote — AI Days 2026 Frankfurt**
*Ein Tag, der zeigt, warum KI nicht ohne den Menschen funktioniert*
📅 28. April 2026 · Frankfurt am Main

**Themenfelder:** KI im Mittelstand · Digitale Transformation · Führung in der Krise

---

## Branchen-Erfahrung

Automotive & Zulieferer · Gesundheit, Kliniken, Versicherungen · Logistik & Schienenverkehr · Behörden & Rüstung · E-Commerce · Hotel & Gastgewerbe · Pharmaindustrie & Chemie · Öffentlicher Sektor · Telekommunikation

---

## Kontakt

| | |
|---|---|
| **DARC Management UG** | Gewerbestr. 37a · 58285 Gevelsberg |
| **Telefon** | 02332 9994020 |
| **E-Mail** | [frank.wichert@darc-mgt.de](mailto:frank.wichert@darc-mgt.de) |
| **Web** | [darc-transform.de](https://darc-transform.de) · [darion-ai.de](https://darion-ai.de) |
| **LinkedIn** | [linkedin.com/in/frank-wichert-5b0017294](https://www.linkedin.com/in/frank-wichert-5b0017294/) |
| **Verfügbarkeit** | 48h einsatzbereit |

---

<div align="center">

*DARC · Digital. Agile. Results. Consulting.*

</div>
