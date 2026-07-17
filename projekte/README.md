<div align="center">

# Projekt- und Referenz-Katalog

**Frank Wichert · Interim Manager · CIO · KI-Architekt**

*Über 80 Projekte in mehr als 20 Jahren. Nachfolgend der durchsuchbare Katalog: aktuelle DARC-Eigenentwicklungen sowie eine Auswahl der Interim-Referenzmandate, Bundeswehr und UAV.*

[![Profil](https://img.shields.io/badge/←_zurück_zum_Profil-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/frank-wichert)
[![Web](https://img.shields.io/badge/darc--transform.de-1F2937?style=for-the-badge&logo=googlechrome&logoColor=white)](https://darc-transform.de)
[![Architektur](https://img.shields.io/badge/darion--architecture-2563EB?style=for-the-badge&logo=github&logoColor=white)](https://github.com/frank-wichert/darion-architecture)

</div>

---

## So findest du dich zurecht

Diese Seite ist zum **Durchsuchen** gebaut. Zwei Wege:

- **Volltext-Suche:** Taste <kbd>f</kbd> (GitHub-Dateisuche) oder <kbd>Strg</kbd>/<kbd>⌘</kbd>+<kbd>F</kbd> im Browser. Suche z. B. nach `KRITIS`, `SAP`, `Migration`, `Gesundheitswesen`, `Task Force` oder einer Jahreszahl.
- **Sprungmarken:** Über die [Master-Übersicht](#master-übersicht) und die [Branchen-Filter](#nach-branche-filtern).

Jeder Eintrag trägt eine `🏷️`-Tag-Zeile mit Rolle, Branche, Thema und Compliance. Die Tag-Legende steht [ganz unten](#tag-legende).

**Inhalt**

1. [DARC-Eigenentwicklungen und KI-Plattformen (seit 08/2024)](#a-darc-eigenentwicklungen-und-ki-plattformen)
2. [Interim-Referenzmandate (Auswahl)](#b-interim-referenzmandate-auswahl)
3. [UAV und Bundeswehr](#c-uav-und-bundeswehr)
4. [DARC-Produkte](#d-darc-produkte)
5. [Master-Übersicht (alle Mandate auf einen Blick)](#master-übersicht)
6. [Nach Branche filtern](#nach-branche-filtern)
7. [Tag-Legende](#tag-legende)

---

## A. DARC-Eigenentwicklungen und KI-Plattformen

> Seit Q3 2024 als Lead Architect mit einem Kernteam (zwei Entwickler plus AI-Pair-Programming): produktive Plattformen und Infrastruktur-Bausteine. Eigenentwicklung mit Pilotkunden, Multi-Tenancy als Fundament, IT-Sicherheit und Compliance von Beginn an. Detaillierte Bausteine und Prinzipien in der öffentlichen [**Architektur-Vitrine**](https://github.com/frank-wichert/darion-architecture).

| # | Projekt | Kurzbeschreibung | Status | Kern-Stack |
|---|---------|------------------|--------|------------|
| 1 | **DARION-AI · Multi-Tenant-SaaS** | Modulare Business-Suite mit 20 Fachmodulen, davon 16 verfügbar (u. a. Finanzen, HR, Vertrieb, Projekte/PSA, Verträge, E-Rechnung, Zeiterfassung, IT-Management, DMS, Wissen, ISMS, DSGVO-Compliance), 4 im Ausbau; Multi-LLM-Routing, RAG-Layer, Live-Cockpit, CNPG-HA mit Pooler, CI/CD ≥ 80 % Coverage | Launch 18.08.2026 | FastAPI · Next.js 15 · K3s · CloudNativePG · RAG · OpenTelemetry |
| 2 | **Zentrale Coding-Plattform (Tina)** | Orchestrierte, autonome Software-Entwicklung mit Gewaltenteilung: lokale Code-Modelle bauen tier-basiert, ein unabhängiges Review-Modell prüft jeden Beitrag, Merge nur über Draft-PR (kein Auto-Merge). Plan-, Critic- und Recall-Rollen, Lern-Loop | Pilot-Loop produktiv | Temporal · vLLM · MCP · Catalyst |
| 3 | **DARION Core · Agenten-Orchestrierung** | Mixture-of-Agents-Framework mit Plan-, Critic- und Recall-Agent plus Orchestrator; Unified Query Hub, Knowledge-Graph, 176 grüne Tests | 6 Phasen produktiv | LiteLLM · Graphiti · Neo4j · MCP · Langfuse |
| 4 | **Wissens-Architektur und Self-Hosted-Wiki** | Souveräner Knowledge-Hub mit SSO und Federation zum Agenten-Wissensspeicher | Produktiv | Outline · Keycloak · Cloudflare Access · PostgreSQL · MinIO |
| 5 | **KI-Governance · Supporter ⇄ Assistenz** | Hart getrennte interne KI-Rollen nach Least-Privilege, in der Datenbank durchgesetzt statt im Prompt, EU-AI-Act-konform | Konzept build-ready | PostgreSQL RLS · JWT · RAG · EU AI Act Art. 50 · Redact-before-Embed |
| 6 | **Identity-, Geheimnis- und Schlüssel-Management** | Dualer Vault-Ansatz mit zweiter Vertrauenslinie, dokumentiertem Schlüssel-Lebenszyklus, Service-Accounts und scoped-Token-Minting | In Betrieb | Vaultwarden · 1Password · OIDC · MFA · TLS · Append-Only |
| 7 | **Server-Cluster mit Mesh-VPN und Tenant-Isolation** | Flotte (VPS plus Bare-Metal CPU/GPU) mit Mesh-VPN, mehrschichtiger Firewall, Reverse-Proxy, WAF und einheitlichem Hardening | In Betrieb | Bare-Metal und VPS · NetBird · WireGuard · Cloudflare WAF · K3s · Caddy |
| 8 | **Configuration-Management und Provisionierung** | Zentrales Inventory aller Mesh-Knoten, idempotente Playbooks (Hardening, SSH, Fail2Ban, Backup), Dry-Run-Workflow mit grüner Verifikation | Phase 5 | Ansible · YAML · Jinja2 · Vault-Lookup · Git |
| 9 | **E2EE-Messaging-Migration** | Vollständige Ablösung von Telegram durch self-hosted Matrix mit Cross-Signing, gehärteter Webhook-API und bewusster Federations-Reduktion | Phasen 1 bis 4 fertig | Matrix-Synapse · Element · matrix-nio · Olm/Megolm · Cross-Signing |
| 10 | **Backup-, Monitoring- und Observability-Stack** | Append-Only-Backup mit Restore-Verifikation und Offsite-Kopie; Live-Cockpit (SSE) für Fleet-Health, LLM-Spend und Heartbeat | In Betrieb | restic · SFTP · PostgreSQL · OpenTelemetry · Prometheus · SSE |
| 11 | **Job-Discovery- und Lead-Enrichment-Pipeline** | Mehrquellige Pipeline mit RAG-Sync, Cross-Host-Review-Oberfläche und regelbasierter Auto-Klassifikation (> 85 %) plus LLM-Restmenge | In Betrieb | FastAPI · PostgreSQL · Apollo · SerpAPI · AnythingLLM |
| 12 | **DARC-Funnel und Marketing-Properties** | Eigenständige Marketing-Sites plus Lead-Funnel mit Selbstcheck-Logik und CRM-Anbindung | Live | Next.js · Cloudflare · Docker Swarm · CRM-Intake |
| 13 | **[DARC System](https://darc-system.de) · Reifegrad-Check und Strategie-Workshop** | Geführtes Self-Assessment für Digitalisierung, KI und Compliance: 8 Module über 3 Ebenen, Reifegrade 0 bis 4, optionaler NIS-2/KRITIS-Check, automatischer PDF-Report | Live | Python · WeasyPrint · YAML · GPG · PDF |
| 14 | **Wissens-gestützte KI-Assistenten · RAG ohne Halluzination** | Assistenz-Bots, die ausschließlich aus dem souveränen Wissensspeicher antworten (RAG plus Knowledge-Graph), mit Weiß-ich-nicht-Fallback und Dual-LLM/CaMeL-Leitplanken | In Betrieb | RAG · pgvector · BGE-M3 · Neo4j · Dual-LLM/CaMeL · LiteLLM |
| 15 | **DARION-AI · Souveräne Cloud-Migration und HA-Betrieb** | Verlagerung der kompletten Umgebung auf souveräne, deutsche Cloud: 3 hochverfügbare Cluster (keine Single-Server), GitOps, verschlüsselte WORM-Backups, verlustfreier Cutover je Domäne · [**Planung, Durchführung und Tests →**](./darion-ai-cloud-migration.md) | Konzept abgeschlossen | RKE2 · Cilium · ArgoCD · CloudNativePG · Terraform · Velero · Kyverno |
| 16 | **DARION-AI Meetings · native Meetings, Transkription und Übersetzung** | In die Plattform integriertes Meetings-Modul mit Live-Audio/Video, Aufzeichnung, automatischer Transkription und Zusammenfassung sowie mehrsprachiger Übersetzung (DE/EN/NL) von Transkript und Protokoll, souverän ohne US-Dienste; Einwilligungs- und Aufzeichnungs-Gate, teilnehmergebundene Zugriffsrechte | Im Ausbau | LiveKit · Whisper · Qwen3 · DeepL · Next.js · PostgreSQL |
| 17 | **Sicherer Dienstleister-Datenaustausch** | Souveräner Datenaustausch Kunde ⇄ Dienstleister direkt in der Plattform: verschlüsselte Freigabe-Links (Download/Upload) und E-Mail-gebundener Gast-Upload mit Einmalcode, revisionssicherem Audit-Trail und zeitlich begrenzten signierten URLs; Eigenbau statt WeTransfer/DRACOON, echte Datenräume als Ausbaustufe | In Entwicklung | PostgreSQL RLS · SECURITY-DEFINER-RPC · Signed URLs · Supabase Storage · Next.js |
| 18 | **KI-Schulung und Nachweis · EU AI Act Art. 4** | Schulungs- und Nachweismodul für KI-Kompetenz (AI-Literacy-Pflicht seit 02/2025): drei rollenbasierte Lernpfade (Basis, Management, Power-User) mit Test, automatischem Zertifikat und prüfsicherem Nachweis je Mitarbeiter in der HR-Ansicht; USP ist der integrierte, revisionssichere Nachweis (Hash-Chain-Audit-Log) | In Entwicklung | PostgreSQL · Hash-Chain-Audit · WeasyPrint · Entitlements · EU AI Act Art. 4 |
| 19 | **DARION-AI Shop · Kundenshop-Modul (B2B)** | Produktkatalog mit Stammdaten, Kategorien und Steuer-FK unter account-scoped RLS, gehärteter API und OpenAPI-Spezifikation; Checkout, Bestellungen und Mollie-Zahlung als Folge-Slices | In Entwicklung | Next.js · PostgreSQL RLS · SECURITY-DEFINER-RPC · OpenAPI · Mollie (geplant) |

🏷️ *Rollen:* Lead Architect · KI-Architektur · Plattform-Engineering · Cloud/K8s · Security by Design · Compliance (DSGVO · EU AI Act · NIS2 · ISO 27001 · BSI C5)

---

## B. Interim-Referenzmandate (Auswahl)

> Antichronologische Auswahl. Alle Angaben mandanten-neutral (branchenweit, ohne Kundennamen). Vollständige Referenzliste auf Anfrage.

### Interim-Leitung IT, Stadtverwaltung
**2025 · 7 Monate · Mitarbeiterverantwortung 15**
Operativer 24/7-Betrieb (Help Desk, Rechenzentrum, Applikationen), Reorganisation und strategische Neuausrichtung der IT-Abteilung, Aufbau eines Providermanagements. Verantwortlich für 3 Schulen und 2 Feuerwehrstandorte, Aufbau von IT-Sicherheitsrichtlinien, Standortvernetzung und Cluster, Einführung Microsoft 365 inkl. Teams, Berichterstattung in Gremien (Hauptausschuss, Schulzweckverband).
`Tech & Methoden:` Rechenzentrum, Cluster, Microsoft Server, Microsoft 365, Exchange, Voice, Fortinet, ITSM, Asset- und Lizenzmanagement, Incident Management, NinjaONE, Task Force, Vertragsverhandlungen.
🏷️ Öffentlicher Sektor · Behörden · IT-Leitung · Reorganisation · Providermanagement · Microsoft 365 · KRITIS · NIS2

### Interim-Leitung IT, Klinikverbund
**2024 · 8 Monate · Mitarbeiterverantwortung 35**
Operativer 24/7-Betrieb, Reorganisation und Aufbau eines Providermanagements, Verantwortung für vier Rechenzentren, Führung von 4 Teams (Service Desk, IT-Infrastruktur, Medizin-IT, Applikation), Aufbau von IT-Sicherheitsrichtlinien, IT-Projektmanagement und Personalgespräche.
`Tech & Methoden:` Rechenzentrum, Microsoft Server, Office 365, KIS (Orbis), RADCenter, Clinic Planner, ITSM, Incident Management, CrowdStrike, Eskalationsmanagement, Task Force.
🏷️ Gesundheitswesen · Kliniken · IT-Leitung · Medizin-IT · KIS/Orbis · KRITIS · NIS2

### Interim-IT-Bereichsleiter / CIO, Gesetzliche Krankenkasse
**2023 bis 2024 · 9 Monate · Mitarbeiterverantwortung 120**
Operativer 24/7-Betrieb, Auf- und Ausbau verschiedener Services sowie Steuerung externer Dienstleister, Verantwortung für zwei Rechenzentren, Budget, Ressourcen, Controlling und Reporting, Coaching und Mentoring, Prozessanpassung nach ITIL, Planung und Einführung von Managed Services und Change-Management, Leitung der Task Force für Eskalations- und Risikomanagement.
`Tech & Methoden:` Rechenzentrum, Microsoft Server, Office 365, KIS Bitmarck, ITSM, Incident Management, Task Force, Vertragsverhandlungen.
🏷️ Versicherung · Gesundheitswesen · CIO · ITIL · Managed Services · Task Force

### Interim-IT-Manager, Gesundheitstechnik (international)
**2023 · 6,5 Monate · Mitarbeiterverantwortung 35**
Übernahme der internen IT-Abteilung mit Office-IT und Produktions-IT, internationales Unternehmen im Bereich Versorgungs- und Gesundheitsinterventionen. 24/7-Betrieb national und international, Abstimmung mit der Muttergesellschaft in UK, Steuerung externer Dienstleister mit Rechenzentren, ERP-Migration, Budget und Controlling, Workshops mit Betriebsrat und Datenschutz (Betriebsvereinbarungen).
`Tech & Methoden:` Rechenzentrum, Microsoft Server, Office 365, Cisco, ERP, Telefonanlage, Asset- und Lizenzmanagement, Home Office, Eskalationsmanagement.
🏷️ Gesundheitstechnik · IT-Leitung · Produktions-IT · ERP-Migration · International

### Interim-Agiler IT-Projektmanager, Öffentlicher Sektor
**2023 · 12 Monate · Mitarbeiterverantwortung 12**
Entwicklung einer neuen, modularen Software zur Digitalisierung von Fördermaßnahmen (technische Dienststelle für Agrarverwaltung). Agile Führung eines Teams von 12 Mitarbeitern, Sprint-Planung mit User Stories, Abstimmung mit mehreren Ministerien und Landesbetrieben, Entscheidungsvorlagen für Gremien, fachliche Tests (UAT) und Abnahme inkl. Freigabe, Dokumentation und Schulung.
`Tech & Methoden:` Scrum, agile Softwareentwicklung, Ausschreibungen, Recruiting, Kotlin, Jira, Confluence, UX, eAkte, ANDI, Onlinezugangsgesetz.
🏷️ Öffentlicher Sektor · Softwareentwicklung · Agile/Scrum · OZG · eAkte

### Interim-Manager, Task-Force-Leitung / Projektsanierung, Logistik (international)
**2023 · 10 Monate · Mitarbeiterverantwortung 40**
Übernahme der Leitung eines Projekts zur Migration von Microsoft 365 und Microsoft Teams (3.500 User). Überarbeitung und Priorisierung der Projektplanung, Aufbau und Führung einer Task Force, Migrationsplanung mit Abhängigkeiten, Adoption- und Change-Management (ACM), Kommunikation und Newsletter, Steuerung von Dienstleistern, Reporting an Lenkungskreis und Vorstand.
`Tech & Methoden:` Microsoft 365, Task Force, Quest, Citrix, SAP, JobRouter, Client-Rollout, Azure, Cloud, Projektcontrolling, CrowdStrike, Service Desk.
🏷️ Logistik · Sanierung · Task Force · Microsoft-365-Migration · Change-Management · International

### Interim-Manager, Leitung IT, Gesundheitsbranche
**2022 · 12 Monate · Mitarbeiterverantwortung 24**
Leitung eines Projekts für die neue Gebührenordnung (GOÄ), Verband der Privaten Krankenversicherung. Ausschreibungsunterlagen für eine verkürzte nationale Ausschreibung, Bieterauswertung und Vertragsgestaltung, mehrere Workshops mit über 50 Teilnehmern, Steuerung von drei Providern, Abstimmung mit über 20 privaten Krankenkassen zur Datenbereitstellung, Aufbau einer Plattform zum Datenaustausch und einer Transkodier-Matrix, Datenbank zur Auswertung von Gebührenziffern.
`Tech & Methoden:` Datenbanksysteme, Webplattformen, Reporting, Jira, Confluence, Ausschreibungen, KI, Projektcontrolling, Vertragserstellung.
🏷️ Gesundheitswesen · Versicherung · Programm-Leitung · Ausschreibung · Datenplattform

### Interim-Multi-IT-Projektmanager, Logistik (international)
**2022 · 8 Monate · Mitarbeiterverantwortung 18**
Leitung mehrerer Projekte in den Bereichen Tendermanagement, Carve-out und IT-Sicherheit. Verantwortlich für sechs Projekte, Budget und Controlling, enge Abstimmung mit internen Abteilungen und Providern, Unterstützung bei Ausschreibungen.
`Tech & Methoden:` Rechenzentrum, Microsoft Server, Office 365, SAP, Cisco, PowerShell, Standortplanung, ITSM, Ausschreibungen, TISAX, ISO 9001, ISO 27001/27002.
🏷️ Logistik · Multi-Projekt · Carve-out · Tender · TISAX · ISO 27001 · International

### Interim-IT-Programmmanager, Pharma (international)
**2022 · 6 Monate · Mitarbeiterverantwortung 45**
Aufbau und Leitung eines Programms zur Umsetzung der IT-Sicherheit im IT-Bereich. Verantwortlich für 5 Projekte, Budget, Controlling und Reporting, Aufbau des Programms und Übergabe an einen internen Programmmanager.
`Tech & Methoden:` Rechenzentrum, Cisco Meraki, SAP, Novell, VMware NSX, VMware Horizon, Jira, Confluence, GxP, Vertragsverhandlungen.
🏷️ Pharma · Programm-Management · IT-Sicherheit · GxP · International

### Interim-Manager, Hafen- und Logistikunternehmen (international)
**2021 · 5,5 Monate**
Vorbereitung einer öffentlichen Ausschreibung für Help Desk, IMAC-Service und Asset-Management. Konzeption und Bearbeitung öffentlicher Ausschreibungen, Aufnahme und Abgleich von Anforderungen, Workshops mit Fachbereichen, Ausschreibungsdokument inkl. Vertrags- und Konventionalstrafen, Abnahme mit dem Fachbereich.
`Tech & Methoden:` Öffentliche Ausschreibung, ITSM, Asset-Management, Anforderungsmanagement.
🏷️ Logistik · Häfen · Ausschreibung · IMAC · Asset-Management · International

### Interim-Manager, Handel / E-Commerce (international)
**2021 · 12 Monate**
Überarbeitung des Projekt- und Portfoliomanagements, Online-Shop sowie Aufbau eines Zentrallagers für Europa in Deutschland. Nachhaltiges Projekt- und Portfoliomanagement, Online-Shop-System mit Anbindung an ein Omnichannel-Marketing-System, Warehouse-Anbindung, europäisches Zentrallager.
`Tech & Methoden:` Shopify, WordPress/WooCommerce, JTL, PlentyONE.
🏷️ Handel · E-Commerce · Portfoliomanagement · Omnichannel · Logistik · International

### Interim-IT-Projektmanager, Automobilhersteller (international)
**2020 · 6 Monate · Mitarbeiterverantwortung 12**
Planung und Umsetzung einer digitalen Kundenplattform. Budget, Controlling und Reporting, Evaluierung von Umfeld, Schnittstellen, Abhängigkeiten und Risiken, Abstimmung mit Automobilherstellern, Vertriebseinheiten, Zulieferern und Autohäusern, Rechtsabteilungen, Umsetzung und Test der neuen Plattform inkl. Schnittstellen.
`Tech & Methoden:` Data Center, SAP, CRM, Schnittstellen, Prozessmanagement, Anforderungsmanagement, Digitalisierung, Eskalationsmanagement.
🏷️ Automotive · Digitale Plattform · CRM · Schnittstellen · International

### Interim-Manager, Gruppe für Umformtechnik (international)
**2020 · 8 Monate · Mitarbeiterverantwortung 25**
Leitung eines Projekts zum Aufbau einer IT-Organisation mit User Help Desk. Entwicklung und Aufbau der Services sowie Erstellung des Target Operating Models, Weiterentwicklung des Service-Katalogs, SLAs, OLAs und KPIs, Aufbau von Business Services im ITSM-Tool und Workplace Management, SLA-Reporting mit KPIs, Schulungskonzept, Coaching.
`Tech & Methoden:` Microsoft Server, Cisco Meraki, SAP, CMDB, TOPdesk, PowerShell, IT-Service-Management, Workplace Management, Omnitracker.
🏷️ Automotive · Umformtechnik · IT-Organisation · ITSM · TOM · SLA/KPI · International

### Interim-Projektmanager, Spezialchemiekonzern (international)
**2020 · 7 Monate · Mitarbeiterverantwortung 18**
Leitung eines Projekts zur Migration von Windows 7 auf Windows 10 (Projektsanierung). Budget und Controlling, Entwicklung eines Windows-10-Clients mit Standard-Applikationen inkl. Test, neue IT-Infrastruktur für Client- und Software-Management, internationale Break-and-Fix-Prozesse, internationaler Rollout und Ressourcenplanung, Schulung des 1st- und 2nd-Level-Supports, Qualitätssicherung, Übergabe in den Betrieb.
`Tech & Methoden:` Windows 10, Microsoft SCCM, Office 365, Azure, IAM, Virtualisierung, PowerShell, Migration, Workplace Management, SLA, OLA, PKI, WLAN.
🏷️ Chemie · Client-Migration · Windows 10 · SCCM · Sanierung · International

### Interim-Transition-Manager, Mobilfunkanbieter (national)
**2020 · 8 Monate · Mitarbeiterverantwortung 22**
Leitung eines Programms für Transition und Outsourcing von Leistungen. Verantwortlich für sechs Projekte, Budget und Controlling, enge Abstimmung mit den Providern, Einhaltung definierter Transitionsprozesse, Aufbau des Programms und Übergabe an einen internen Programmmanager.
`Tech & Methoden:` Genesys, NetScaler, mCIS, mCBS, Citrix, Data Center, Mobilfunk, Virtualisierung, Ausschreibungen, Migration, Workplace Management, Omnichannel, Chatbot.
🏷️ Telekommunikation · Transition · Outsourcing · Programm-Management · National

### Interim-IT-Programmmanager, Automobilzulieferer (international)
**2019 · 6 Monate · Mitarbeiterverantwortung 36**
Leitung eines Programms zur Umsetzung der DSGVO (GDPR) im IT-Bereich. Verantwortlich für neun Projekte mit über 5 Workstreams, Budget, Controlling und Reporting, Aufbau des Programms und Übergabe an einen internen Programmmanager.
`Tech & Methoden:` SAP HR, IdM/IAM, ServiceNow, IT-Dokumentation, IT-Service-Management, Workplace Management.
🏷️ Automotive · DSGVO/GDPR · Programm-Management · IAM · International

### Interim-Projektmanager, Automobilzulieferer (international)
**2019 · 8 Monate**
Planung eines Rechenzentrumsumzugs mit 18.000 Servern und Data-Center-Konsolidierung. Evaluierung von Umfeld und Stakeholdern/Providern, Planung und Roadmap (Release Train), Aufbau einer Interims-Datenbank für den Umzug, Kommunikationsplan mit Tracking und Reporting, Hardware-Release-Management und Hardware-Austausch.
`Tech & Methoden:` Cluster, Windows Server, UNIX, Linux, AIX, VMware, Storage, Netzwerk, Load Balancer, Middleware, SAP, CRM, ERP, FNT-Command, SAFe, IoT, KPI.
🏷️ Automotive · Rechenzentrum · Data-Center-Konsolidierung · 18.000 Server · SAFe · International

### Interim-Programmmanager, Windenergie (international)
**2018 · 8 Monate · Mitarbeiterverantwortung 110**
Leitung eines Programms zur Implementierung einer PLM/PDM-Software. Verantwortlich für 6 Projekte mit über 30 Workstreams, Budget, Controlling und Reporting, Stakeholder-Management und Management of Change, Supply-Chain-Management, Lean Management, Qualitätsmanagement.
`Tech & Methoden:` Windchill, SAP, ZEUS, CAD-Systeme, ERP, PLM/PDM, PowerFactory, ServiceNow, Datenmigration, Rollout, IoT.
🏷️ Energie · Windenergie · PLM/PDM · Programm-Management · Change · International

### Interim-Projektmanager, Logistik (international)
**2018 · 4 Monate**
Implementierung einer Controlling-Software. Anforderungsmanagement und Konzepterstellung, Erarbeitung von Prozessen und Freigabeinstanzen, Anbieter-Evaluierung und Implementierung, Überführung der Daten in das neue System und Abnahme, Schulung von Führungskräften, Einhaltung BSI-Grundschutz, ISO 9001 und ISO 27001.
`Tech & Methoden:` Controlling-Software, Prozessdesign, Supply-Chain-Management, Lean Management, BSI-Grundschutz, ISO 9001, ISO 27001.
🏷️ Logistik · Controlling-Software · Prozesse · ISO 27001 · International

### Interim-Projektmanager, Photovoltaik-Hersteller (international)
**2018 · 6 Monate · Mitarbeiterverantwortung 12**
Transition und Outsourcing des Data Centers. Anforderungsanalyse und Workshops, Evaluierung der Data-Center-Komponenten, Abstimmung mit Dienstleistern/Providern, Transitionsplanung und Roadmap, System- und Softwareübersicht, Aufbau eines Transition-Boards und Eskalationsprozesses, Definition von SLAs und Sicherheitsvorgaben, Transition der Systeme und Übergabe.
`Tech & Methoden:` Jira, Microsoft Server und Clients, VMware, Cisco, Netzwerk, WLAN, Load Balancer, Firewall, PowerShell, ITSM, Migration, Workplace Management, IoT, KPI.
🏷️ Energie · Photovoltaik · Data-Center-Transition · Outsourcing · SLA · International

### Interim-Manager / COO, Softwareentwicklung (SaaS, Mittelstand)
**2017 · 10 Monate · Mitarbeiterverantwortung 32**
Softwareentwicklung für SaaS in einem mittelständischen Unternehmen. Anforderungs- und User-Story-Management, Planung und Roadmap, Kommunikation mit agilem Team, Steering Committee und externen Dienstleistern, Sprint-, Test- und Integrationsplanung, Führung des agilen Teams, Implementierung eines Qualitätsmanagements mit Unit-Tests und Software-Integration, Produktpakete und Preise, Marketing- und Vertriebskonzepte, Konzeption eines Marketplace.
`Tech & Methoden:` Jira, Sprints, virtuelle Teams, Kanban, Migration.
🏷️ SaaS · Mittelstand · COO · Produktmanagement · Agile · Go-to-Market

### Interim-Projektmanager, Logistik (international)
**2017 · 4 Monate**
Implementierung eines Dokumentenmanagementsystems (DMS). Anforderungsmanagement und Kommunikationsstrategie, Konzepterstellung sowie Ausschreibungsunterlagen und Bewertungsmatrix, Anbieterpräsentationen, Evaluierung und Prüfung des Pflichtenhefts, Implementierung des DMS, Einhaltung BSI-Grundschutz, ISO 27001 und ISO 27002.
`Tech & Methoden:` Jira, Confluence, ERP, E-Commerce, PLM/PDM, IT-Dokumentation.
🏷️ Logistik · DMS · Ausschreibung · ISO 27001 · International

### Interim-Programmmanager, Logistik (international)
**2016 · 8 Monate**
Demand- und Produktportfolio-Management. Anforderungsmanagement sowie Überarbeitung und Implementierung von Prozessen, Evaluierung und Beratung von Produkten, Ausschreibung und Implementierung von Produkten, Erstellung von Business Cases und Wirtschaftlichkeitsdarstellung, Koordination von Projekten und Auditierung von Projektmanagement-Standards.
`Tech & Methoden:` Jira, Confluence, ERP, E-Commerce, CRM, Salesforce, Personaleinsatzplanung, ITSM, Workplace Management.
🏷️ Logistik · Demand-Management · Portfolio · Business Cases · International

### Interim-Projektmanager, IT-Dienstleister (international)
**2016 · 4 Monate**
Erstellung und Implementierung eines modularen Produktkatalogs für Managed-Service-Leistungen. Portfolioanalyse und Anforderungsmanagement, Auswertung der Leistungen und Alleinstellungsmerkmale, Markt- und Wettbewerbsanalyse inkl. Benchmarking, Strategieworkshop zur Neuausrichtung, modularer Produktkatalog, SLAs und OLAs, Aufbau einer CMDB, Schulung des Managements und Übergabe.
`Tech & Methoden:` Jira, Confluence, ERP, E-Commerce, ServiceNow, ITSM, Workplace Management, KPI, BSI-Grundschutz, ISO 27001/27002.
🏷️ IT-Dienstleister · Managed Services · Produktkatalog · Strategie · CMDB · International

### Interim-Projektmanager, Automobilzulieferer (international)
**2015 · 6 Monate**
Implementierung und Betrieb eines Demand-Management-Systems. Analyse vorhandener Prozesse und Abläufe, Sammlung und Auswertung von Anforderungen, Vorgaben und Verträgen, Entwicklung des Ablaufprozesses für das Demand Management, Implementierung des Systems und Integration des Ablaufprozesses.
`Tech & Methoden:` Demand-Management-System, Prozessdesign, Supply-Chain-Management, Lean Management.
🏷️ Automotive · Demand-Management · Prozesse · International

### Interim-Projektmanager, Luftsicherheit (international)
**2015 · 6 Monate**
Anpassung der Prozesse nach Paragraf 5 LuftSiG an den Flughäfen Hamburg, Hannover und Frankfurt. Analyse vorhandener Prozesse und Abläufe, Sammlung und Auswertung von Anforderungen, Vorgaben und Verträgen, Abstimmung mit der Bundespolizei, Anpassung der Abläufe und Schulung des verantwortlichen Personals, Integration neuer Ablaufprozesse.
`Tech & Methoden:` LuftSiG §5, Prozessanpassung, Behörden-Abstimmung, Schulung.
🏷️ Luftsicherheit · Flughäfen · LuftSiG · Behörden · Compliance · International

### Interim-Projektmanager, Automobilzulieferer (international)
**2015 · 5 Monate**
Implementierung und Betrieb eines Remote-Server-Management-Systems. Umgebungsanalyse und Anforderungsmanagement, Auswertung der Verträge mit SLAs und OLAs, Evaluierung eines Remote-Management-Systems, Planung und Aufbau eines Follow-the-Sun-Supports, Standardprozesse und Qualitätsmaßnahmen, Schichtbetrieb inkl. Rufbereitschaft, Schulung der IT-Abteilung, Einhaltung BSI-Grundschutz, ISO 27001 und ISO 27002.
`Tech & Methoden:` Remote-Server-Management, Follow-the-Sun-Support, SLA/OLA, BSI-Grundschutz, ISO 27001/27002.
🏷️ Automotive · Remote-Management · Follow-the-Sun · ISO 27001 · International

### Interim-Projektmanager, Bank / Automotive (international)
**2014 · 8 Monate**
Aufbau und Betrieb eines Project Management Office mit Demand Management, internationaler Automobilhersteller mit interner Bank. Analyse vorhandener Prozesse und Abläufe, Anforderungsmanagement, Stakeholder-Management, Standard-Ablaufprozess für Projekte, Standardisierung von Portfolio- und Programm-Management, Evaluierung einer Projektmanagement-Software und Integration der Prozesse, Schulung der Projektleiter und Übergabe.
`Tech & Methoden:` PMO, Demand Management, Portfolio- und Programm-Management, PM-Software, Standardisierung.
🏷️ Banken · Automotive · PMO · Demand-Management · Standardisierung · International

### Interim-Projektmanager, Mittelstand (international)
**2014 · 6 Monate**
Umzug des internen Rechenzentrums. Analyse des Rechenzentrums und Anforderungsmanagement, Umzugsplanung und Technologie-Beratung für Server und Netzwerk inkl. WLAN, Konzepterstellung (Shutdown, Übernahme, Inbetriebnahme), Koordination von Facility Management, Logistik und IT-Abteilung sowie Providern, Abbau und Aufbau des Rechenzentrums und Übergabe, Risk-Management, Controlling, Reviews und Audits nach BSI-Grundschutz, ISO 27001 und ISO 27002.
`Tech & Methoden:` Rechenzentrumsumzug, Server, Netzwerk, WLAN, Facility Management, Risk-Management, BSI-Grundschutz, ISO 27001/27002.
🏷️ Mittelstand · Rechenzentrumsumzug · Infrastruktur · ISO 27001 · International

---

## C. UAV und Bundeswehr

### UAV (Unmanned Aerial Vehicle, < 25 kg), Dienstleistung
**2015 bis 2017 · 18 Monate**
Aufbau und Entwicklung unbemannter Flugsysteme, Schulung und Ausbildung mit Webinaren (LuftVO Paragraf 21), UAV-Traffic-Management und Unterstützung der Flugplanung, BVLOS (Beyond Visual Line of Sight) / Langstreckenflug, Bild- und Video-Liveübertragung über Funk- und IP-Netze, GPS, Vermessung, Punktwolken und 3D-Bilderstellung (ArcGIS), Sicherheits- und Risikobewertung nach SORA (Specific Operations Risk Assessment).
🏷️ UAV/Drohnen · BVLOS · SORA · LuftVO · Vermessung/3D · ArcGIS

### Zeitsoldat / Abteilungsleiter, Bundeswehr
**2003 bis 2015 · 12 Jahre · Verantwortung für 30 bis 150 Soldaten**
Verantwortlich für zwei Rechenzentren, Leitung mehrerer Kommunikations-Trupps im Auslandseinsatz mit Anbindung an Fremd-Truppenteile, Leitung von Fahrzeug- und Träger-Umbauten inkl. Funktionstests, Aufbau und Betrieb einer Server-Infrastruktur auf einem Flughafen, Aufbau und Betrieb eines User Help Desks, Entwicklung einer Virtualisierungsstufe für die Bundeswehr / BWI, vier Auslandseinsätze.
`Tech & Methoden:` SatCom, Tetrapol, Funktechnik (SEM52S/SL, SEM90, SEM93), FüInfoSys Heer, NuKomBW, Kryptoverschlüsselung, Microsoft Server, Storage, Lotus Notes Domino, SASPF/R3.
🏷️ Behörden/Defence · Bundeswehr · Führung · Rechenzentrum · Auslandseinsatz · KRITIS

---

## D. DARC-Produkte

> Produkte der DARC Management UG rund um souveräne KI und Digitalisierung.

### DARC One · Souveräner KI-Assistent
**Status: Live** · [darc-transform.de/darc-one](https://darc-transform.de/darc-one/)
Self-hosted KI-Assistent für den regulierten Mittelstand (Steuerkanzleien, Rechtsanwälte, Arztpraxen, Versicherungsvermittler, datenschutzsensible Betriebe). Erreichbar über Telefon, Website-Chat und Matrix, betrieben in Deutschland ohne US-Dienste.
**Mehrwert:** Macht Compliance zu einer technischen Eigenschaft des Systems statt zu bloßer Dokumentation. Ein Governance-Gate prüft jede Aktion vor der Ausführung, Auskünfte sind belegt statt halluziniert, jede Aktion landet in einem signierten Audit-Log, Konnektoren (z. B. DATEV) bleiben read-only, und Hochrisiko-Aktionen bleiben Human-in-the-Loop. EU-AI-Act-konform ab Tag 1.
🏷️ KI-Assistent · Governance-Gate · Audit-Log · RAG · EU AI Act · self-hosted · regulierter Mittelstand

### DARC Suite · Self-hosted Business-Suite
**Status: In Betrieb**
Self-hosted Business-Suite für KMU mit CRM, Projekten, HR, Recruiting und Rechnungsstellung, betrieben und gehärtet auf eigener Infrastruktur in Deutschland.
**Mehrwert:** Deckt die operativen Kernprozesse vom Vertrieb bis zur Faktura in einer souveränen Umgebung ohne US-Cloud ab, mit gehärtetem Betrieb (Least-Privilege, Backups, Monitoring).
🏷️ Business-Suite · CRM · HR · Recruiting · Faktura · self-hosted · KMU

### DARC System · Reifegrad-Check und Strategie-Workshop
**Status: Live** · [darc-system.de](https://darc-system.de)
Geführtes Self-Assessment für Digitalisierung, KI und Compliance: 8 Module über 3 Ebenen (inklusive „Führung mit KI"), Reifegrade 0 bis 4, optionaler NIS-2/KRITIS-Betroffenheits-Check, automatisch erzeugter PDF-Report mit RACI- und Schichtenmodell, dazu ein begleitender Strategie-Workshop zur Einordnung der Ergebnisse.
**Mehrwert:** Objektive Standortbestimmung mit konkreter Maßnahmen-Roadmap statt Bauchgefühl, inklusive regulatorischer Betroffenheit (NIS 2, KRITIS).
🏷️ Assessment · Reifegrad · NIS2/KRITIS · Strategie · PDF-Report

---

## Master-Übersicht

*Alle Referenzmandate auf einen Blick, antichronologisch. Für Details in die jeweilige Sektion springen oder oben per Suche filtern.*

| Jahr | Mandat / Rolle | Branche | Team | Schwerpunkt-Tags |
|------|----------------|---------|:----:|------------------|
| 2025 | Interim-Leitung IT | Öffentlicher Sektor | 15 | Reorganisation · Microsoft 365 · KRITIS |
| 2024 | Interim-Leitung IT | Gesundheitswesen (Klinik) | 35 | Medizin-IT · KIS/Orbis · NIS2 |
| 2023-24 | Interim-Bereichsleiter / CIO | Versicherung / GKV | 120 | CIO · ITIL · Managed Services |
| 2023 | Interim-IT-Manager | Gesundheitstechnik | 35 | Produktions-IT · ERP-Migration |
| 2023 | Interim-Agiler IT-PM | Öffentlicher Sektor | 12 | Softwareentwicklung · Scrum · OZG |
| 2023 | Task-Force-Leitung / Sanierung | Logistik | 40 | Microsoft-365-Migration · Task Force |
| 2022 | Interim-Leitung IT | Gesundheitswesen / PKV | 24 | Ausschreibung · Datenplattform |
| 2022 | Multi-IT-PM | Logistik | 18 | Carve-out · TISAX · ISO 27001 |
| 2022 | IT-Programmmanager | Pharma | 45 | IT-Sicherheit · GxP |
| 2021 | Interim-Manager | Logistik (Häfen) | – | Ausschreibung · IMAC · Asset-Mgmt |
| 2021 | Interim-Manager | Handel / E-Commerce | – | Portfolio · Omnichannel · Zentrallager |
| 2020 | Interim-IT-PM | Automotive | 12 | Digitale Plattform · CRM |
| 2020 | Interim-Manager | Automotive (Umformtechnik) | 25 | IT-Organisation · ITSM · TOM |
| 2020 | Interim-PM | Chemie | 18 | Windows-10-Migration · SCCM · Sanierung |
| 2020 | Transition-Manager | Telekommunikation | 22 | Transition · Outsourcing |
| 2019 | IT-Programmmanager | Automotive | 36 | DSGVO/GDPR · IAM |
| 2019 | Interim-PM | Automotive | – | RZ-Umzug · 18.000 Server · SAFe |
| 2018 | Programmmanager | Energie (Wind) | 110 | PLM/PDM · Change |
| 2018 | Interim-PM | Logistik | – | Controlling-Software · ISO 27001 |
| 2018 | Interim-PM | Energie (Photovoltaik) | 12 | Data-Center-Transition · SLA |
| 2017 | Interim-Manager / COO | SaaS / Mittelstand | 32 | Produktmgmt · Agile · Go-to-Market |
| 2017 | Interim-PM | Logistik | – | DMS · Ausschreibung · ISO 27001 |
| 2016 | Programmmanager | Logistik | – | Demand-Mgmt · Portfolio |
| 2016 | Interim-PM | IT-Dienstleister | – | Managed Services · Produktkatalog · CMDB |
| 2015 | Interim-PM | Automotive | – | Demand-Management-System |
| 2015 | Interim-PM | Luftsicherheit | – | LuftSiG §5 · Behörden |
| 2015 | Interim-PM | Automotive | – | Remote-Management · Follow-the-Sun |
| 2014 | Interim-PM | Banken / Automotive | – | PMO · Demand-Management |
| 2014 | Interim-PM | Mittelstand | – | RZ-Umzug · ISO 27001 |
| 2015-17 | UAV-Dienstleistung | Luftfahrt / Vermessung | – | BVLOS · SORA · 3D |
| 2003-15 | Zeitsoldat / Abteilungsleiter | Behörden / Defence | 30-150 | Führung · Rechenzentrum · Auslandseinsatz |

---

## Nach Branche filtern

- **Gesundheitswesen, Kliniken, Versicherungen:** Klinikverbund (2024) · GKV/CIO (2023-24) · Gesundheitstechnik (2023) · PKV/GOÄ (2022)
- **Öffentlicher Sektor, Behörden, Defence:** Stadtverwaltung (2025) · Agrarverwaltung (2023) · Luftsicherheit (2015) · Bundeswehr (2003-15)
- **Automotive und Zulieferer:** Kundenplattform (2020) · Umformtechnik (2020) · DSGVO-Programm (2019) · RZ-Umzug 18.000 Server (2019) · Demand-System (2015) · Remote-Management (2015) · Bank/Automotive PMO (2014)
- **Logistik und Schienenverkehr:** M365-Sanierung (2023) · Multi-Projekt/Carve-out (2022) · Häfen (2021) · Controlling-Software (2018) · DMS (2017) · Demand/Portfolio (2016)
- **Pharma und Chemie:** Pharma IT-Sicherheit (2022) · Spezialchemie Windows-10 (2020)
- **Energie:** Windenergie PLM/PDM (2018) · Photovoltaik Data-Center (2018)
- **Handel und E-Commerce:** Portfolio/Omnichannel/Zentrallager (2021)
- **Telekommunikation:** Transition/Outsourcing (2020)
- **IT-Dienstleister und SaaS:** Managed-Service-Katalog (2016) · SaaS-COO (2017)
- **Luftfahrt und Vermessung:** UAV-Dienstleistung (2015-17)

---

## Tag-Legende

Die `🏷️`-Zeilen nutzen durchgängig diese Kategorien, damit die Volltext-Suche zuverlässig trifft:

- **Rolle:** CIO · IT-Leitung · Programm-Management · Projekt-Management · Task-Force · Transition-Manager · COO · Lead Architect
- **Branche:** Gesundheitswesen · Versicherung · Öffentlicher Sektor · Behörden/Defence · Automotive · Logistik · Pharma · Chemie · Energie · Handel/E-Commerce · Telekommunikation · IT-Dienstleister · SaaS · Luftfahrt
- **Thema:** Sanierung · Migration · Rechenzentrum/Data-Center · ITSM/Service-Management · Ausschreibung/Tender · DSGVO · IT-Sicherheit · Carve-out · ERP · PLM/PDM · Cloud · KI · Digitalisierung
- **Compliance:** KRITIS · NIS2 · ISO 27001 · ISO 9001 · TISAX · BSI-Grundschutz · GxP · LuftSiG · EU AI Act · BSI C5

---

<div align="center">

[![← zurück zum Profil](https://img.shields.io/badge/←_zurück_zum_Profil-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/frank-wichert)
[![Termin buchen](https://img.shields.io/badge/📅_Termin_buchen-2563EB?style=for-the-badge)](https://book.darion-ai.de)

*DARC Management UG · Gevelsberg · [darc-transform.de](https://darc-transform.de)*

</div>
