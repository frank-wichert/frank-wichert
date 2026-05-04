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

> *Seit Q3 2024 baue ich als Lead Architect mit einem Kernteam (zwei Entwickler plus AI-Pair-Programming) zehn produktive Plattformen und Infrastruktur-Bausteine auf. Eigenentwicklung mit Pilotkunden, Multi-Tenancy als Fundament, IT-Sicherheit und Compliance von Beginn an mitgedacht.*

### ⚡ DARION — Multi-Tenant SaaS für HR & Projekt-Management mit KI · *Soft-Launch Q2 2026*
Modulare SaaS mit vier Fachmodulen, Multi-LLM-Routing (Claude + lokales LLM), RAG-Layer, Live-Cockpit und CI/CD-Pipeline mit ≥80 % Coverage.
`FastAPI` `Next.js 15` `K3s` `Claude API` `RAG` `OpenTelemetry`

### ⚡ Multi-Tenant Voice-AI-SaaS für B2B-Vermietung · *Pilotphase Q2 2026*
Mandantenfähige Voice-Plattform mit SIP-Trunk, sechs-stufigem Conversational-Design, DSGVO-Voice-Consent (<1s TTFB) und MCP-basierter Halluzinations-Detection.
`Twilio` `Pipecat` `Whisper` `ElevenLabs` `Claude` `MCP`

### ⚡ DARION Core — KI-Agenten-Orchestrierung mit RAG & Knowledge-Graph · *6 Phasen produktiv*
Mixture-of-Agents-Framework mit Plan-, Critic-, Recall-Agent und Orchestrator. Unified Query Hub mit sechs Routen, Knowledge-Graph (Graphiti/Neo4j), 176 grüne Tests.
`Claude` `LiteLLM` `Graphiti` `Neo4j` `MCP` `Langfuse`

### 🔄 Paperclip — KMU-Knowledge-Hub mit RAG · *Q3 2024 – Q2 2026 (Ablösung)*
RAG-basierter Knowledge-Hub mit ca. 22 spezialisierten Agenten, Self-Hosted-LLM (Ollama/Qwen) plus Cloud-Fallback und Web-Recherche-Pipeline mit Lead-Enrichment.
`AnythingLLM` `Ollama` `Qwen 2.5` `Apollo` `SerpAPI` `n8n`

### ⚡ Self-Hosted Identity-, Geheimnis- und Schlüssel-Management · *In Betrieb*
Dualer Vault-Ansatz mit zweiter Vertrauenslinie für besonders schützenswerte Geheimnisse, dokumentiertem Schlüssel-Lebenszyklus und Reaktionsprozess für Geheimnis-Leaks.
`Vaultwarden` `1Password` `OIDC` `MFA` `TLS` `Append-Only`

### ⚡ Multi-Standort-Server-Cluster mit Mesh-VPN & Tenant-Isolation · *In Betrieb*
Server-Flotte (5 VPS + 2 Bare-Metal CPU/GPU) in Frankfurt mit Mesh-VPN, Reverse-Proxy-Layer, Cloudflare WAF und konsistentem Hardening-Profil über alle Knoten.
`Hetzner` `Netbird` `WireGuard` `Cloudflare WAF` `K3s` `Caddy`

### 🔧 Configuration-Management & Provisionierung · *Phase 5*
Zentrales Inventory aller Mesh-Knoten, idempotente Playbooks für Hardening, SSH, Fail2Ban, Backup-Setup. Dry-Run-Workflow mit grüner Verifikation aller Knoten.
`Ansible` `YAML` `Jinja2` `Vault-Lookup` `Git`

### ⚡ Migration auf Ende-zu-Ende-verschlüsseltes Messaging · *Phasen 1–4 abgeschlossen*
Vollständige Ablösung von Telegram durch self-hosted Matrix-Server mit Cross-Signing, gehärteter Webhook-API mit Themenkanälen und bewusster Federations-Reduktion.
`Matrix-Synapse` `Element` `matrix-nio` `Olm/Megolm` `Cross-Signing`

### ⚡ Backup-, Monitoring- und Observability-Stack · *In Betrieb*
Append-Only-Backup mit Restore-Verifikation und Offsite-Kopie. Live-Cockpit über Server-Sent Events für Fleet-Health, LLM-Spend, Backup-Status und Heartbeat.
`restic` `SFTP` `PostgreSQL` `OpenTelemetry` `SSE` `systemd`

### ⚡ Job-Discovery- & Lead-Enrichment-Pipeline · *In Betrieb*
Mehrquellige Pipeline (Apollo, SerpAPI, BA-für-Arbeit) mit RAG-Synchronisation, Cross-Host-Review-Oberfläche und regelbasierter Auto-Klassifikation (>85 %) plus LLM-Restmenge.
`FastAPI` `PostgreSQL` `Apollo` `SerpAPI` `BA-API` `AnythingLLM`

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
