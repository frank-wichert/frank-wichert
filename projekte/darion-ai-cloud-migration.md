# DARION-AI — Souveräne Cloud-Migration & HA-Betrieb

> Verlagerung der kompletten **DARION-AI**-Umgebung auf eine souveräne, europäische Cloud-Infrastruktur.
> Leitprinzip: **gesichert, verhaltensgleich, störungsfrei und jederzeit rollback-fähig** — sowie **nachhaltig** im Aufbau und Betrieb.

Diese Seite vertieft den Profil-Eintrag und beschreibt **Zielbild, Planung, Durchführung und Tests**.

---

## 1. Worum es geht

Die gesamte KI- und Plattform-Umgebung von DARION-AI wird von der bestehenden Cloud-Plattform auf eine **souveräne, deutsche Cloud-Infrastruktur** überführt und die Altumgebung anschließend abgeschaltet. Es handelt sich um eine **Vollmigration**, nicht um Dauer-Parallelbetrieb: gespiegelt wird nur in der Übergangsphase.

**Treiber:**

1. **Digitale Souveränität & Compliance** (DSGVO, NIS2-Relevanz, ISO-27001-Ziel, BSI C5).
2. **Entkopplung vom Anbieter-Klumpenrisiko** (Resilienz gegenüber Einzelabhängigkeiten).
3. **Robustheit:** keine Single-Server mehr, alles redundant.

Die eigentlichen Nutzdaten sind klein (deutlich unter 15 GB). Der Aufwand liegt nicht im Datenvolumen, sondern in **Orchestrierung, Reihenfolge und Netz-Cutover** über mehrere Betriebsdomänen hinweg. Zeithorizont: rund **3 bis 4 Monate**.

---

## 2. Zielarchitektur: 3 HA-Cluster statt Einzelserver

Konsolidierung auf **drei hochverfügbare Kubernetes-Cluster**, geschnitten nach Umgebung:

| Cluster | Inhalt | Schutzstufe |
|---|---|---|
| **prod** | KI-Plattform (Core, RAG, Orchestrierung, LLM-Gateway, Daten), Chat, Steuerung/Operations, CMDB, Marketing, Datenbanken | höchste |
| **non-prod** | Staging und Dev, strikt von Prod getrennt | mittel |
| **mgmt** | GitOps, Observability, Container-Registry, Secrets, Backup, Security-Tooling | zentrale Kontrollebene |

**Hochverfügbarkeit:** Control-Plane mit **3 etcd-Knoten über 3 getrennte Fehlerdomänen** (deutsche Rechenzentrums-Standorte). Der Ausfall eines kompletten Standorts behält das Quorum. Worker über mehrere Standorte, Workloads mit mindestens 2 bis 3 Replicas und Anti-Affinity.

**Betriebs-Stack (alles offen, portabel, kein Vendor-Lock-in):**

- **Substrat:** self-managed **RKE2** (CIS-gehärtet) auf VMs.
- **GitOps:** **ArgoCD** (App-of-Apps, ApplicationSets über alle drei Cluster).
- **Netz/Security:** **Cilium** (eBPF) mit default-deny NetworkPolicies und Hubble.
- **Policy-as-Code:** **Kyverno** mit Pod Security Standards „restricted".
- **Postgres-HA:** **CloudNativePG** in-cluster (Primary plus Replicas je Datenbank).
- **Secrets:** **External Secrets Operator**, Geheimnisse nie im Klartext in Git.
- **Backup/DR:** **Velero** plus CloudNativePG Continuous Backup.
- **Registry:** self-hosted **Harbor** mit CVE-Scan und Signatur-Enforcement.
- **IaC:** **Terraform** plus cloud-init/Ansible-Bootstrap.

K8s-untaugliche Dienste (Mail, coturn, Bastion) laufen als **2-Node-HA außerhalb** der Cluster, also ebenfalls redundant. GPU-Inferenz läuft **on-demand**.

---

## 3. „Gesichert": Sicherheits- und Rollback-Konzept

Sicherheit ist Fundament ab Tag 1, nicht Nacharbeit:

- **RKE2 CIS-Hardening-Profil**, Pod Security „restricted", **default-deny** im Netz, Trust-Zonen je Namespace.
- **RBAC least-privilege**, SSO für Steuerungs-Oberflächen, der mgmt-Cluster ist netz-isoliert.
- **Zugriffs-Sicherheit über eine Access-Plane (Teleport)** mit kurzlebigen Zertifikaten und Session-Audit, scharfgeschaltet **vor** den produktiven Migrationen.
- **Verschlüsselung:** Datenbank-Volumes mit LUKS und eigenem Key-Management, Backups als **unveränderliche WORM-Kopien (Object-Lock), dual-region** über zwei Standorte.
- **Lieferkette:** CVE-Scan und Signatur-Enforcement in der Registry, statische Code-Analyse.
- **Egress-Kontrolle:** nur ein einziger Namespace (LLM-Gateway) darf nach außen, mit DLP-/Redaction-Gate vor Modell-Aufrufen (PII und Geschäftszahlen werden vorab maskiert).
- **Souveräner Ingress:** TLS-Termination ausschließlich im Cluster (eigene Zertifikate), kein Drittanbieter im Kundendaten-Pfad.
- **Verlustfreier Rollback:** Beim Daten-Cutover wird sofort **rückwärts repliziert**, solange das Beobachtungsfenster läuft. Ein Rollback verliert damit **keinen** seit dem Cutover entstandenen Schreibvorgang.

---

## 4. „Nachhaltig": Modularität, Zukunftsfähigkeit, Effizienz

**Modular aufgebaut (4-Schichten-Modell, je eigener GitOps-Pfad, bottom-up mit Verify-Gate):**

| Schicht | Inhalt | Verify-Gate (Beispiel) |
|---|---|---|
| **L0 — Infrastruktur** | VMs, VLANs, Load-Balancer, DNS, Object-Storage (Terraform) | `terraform plan` = 0 Drift, Knoten im Mesh erreichbar |
| **L1 — System/Cluster** | RKE2 (CIS), Cilium, Storage-CSI, cert-manager, External Secrets | kube-bench grün, etcd-Quorum über 3 Domänen, default-deny aktiv |
| **L2 — Plattform-Services** | CloudNativePG, OpenTelemetry, Gateway API, Velero, Registry, Kyverno | Operatoren ready, Backup-Restore-Probe, Policy enforce |
| **L3 — Application** | DARION-AI-Namespaces (Core, RAG, Orchestrierung, LLM-Gateway, Daten, Chat, CMDB, Marketing, Datenbanken) | je Domäne Smoke + Datenkonsistenz |

Ein wiederverwendbares **„Cluster-Bootstrap-Modul"** erzeugt alle drei Cluster identisch (neuer Cluster in Stunden reproduzierbar). Updates laufen gesteuert (system-upgrade-controller, Renovate), Drift erkennt ArgoCD. Der Austausch eines Bausteins bleibt auf seine Schicht begrenzt.

**Zukunftsweisend (Platform-Engineering):** OpenTelemetry (vendor-neutral, kein Observability-Lock-in), **Inference-Gateway** vor dem LLM-Layer (Modell-Routing, Token-Rate-Limiting), deklarative GPU-Zuteilung (DRA), Cluster-API-ready. Eine Internal Developer Platform mit Golden Paths ist bewusst als **Tag-2-Track nach** der Kern-Migration eingeplant.

**Effizienz:** GPU läuft **on-demand** (Modellgewichte auf günstigem Standby-Volume, automatisches An-/Abschalten um die Nutzungsfenster). Das spart in der Startphase grob **80 bis 95 %** der GPU-Kosten gegenüber Dauerbetrieb. Knoten-Konsolidierung in non-prod/mgmt senkt die Grundlast, ohne HA aufzugeben (3-Knoten-etcd bleibt). 100 % Ökostrom in den Ziel-Rechenzentren.

---

## 5. Planung (Wellenplan)

Inkrementell, Domäne für Domäne, Staging-Pilot als Generalprobe, Rollback je Welle.

| Block | Wellen | Inhalt |
|---|---|---|
| **0 — Fundament** | W0–W1 | Account/Quota, GPU-Antrag mit Vorlauf, Terraform-Foundation (Netz + erste VM) |
| **I — Foundation (mgmt zuerst)** | W2–W5 | RKE2-Bootstrap + CIS, Cilium (default-deny), ArgoCD + App-of-Apps, External Secrets |
| **II — Security + Access + Pilot** | W6–W8, WT | Observability/OpenTelemetry, Kyverno + Supply-Chain, Teleport-Access-Plane, **non-prod-Cluster = Staging-Pilot (Generalprobe inkl. Rollback)** |
| **III — Prod-Substrat + Domänen** | W9–W15 | Prod-Substrat + DB-Node-Pool, Registry zuerst, CloudNativePG-DBs + Datenimport, Chat-Domäne, KI-Plattform (RAG/Core/LLM-Gateway, größte Domäne), Assistenz-Dienste (A und B getrennt), Steuerung/Operations, k3s-Apps/CMDB/Marketing |
| **IV — Externe HA + GPU + Abschluss** | W16–W18 | Mail + coturn als 2-Node-HA außerhalb K8s, souveräner GPU-Tier (warm zu Arbeitszeiten + on-demand), **Verifikation + Abschaltung der Altumgebung** |
| **V — Tag-2** | Phase 8 | Internal Developer Platform (Backstage, Golden Paths, Preview-Envs) nach der Kern-Migration |

**Schicht-Gates:** Jede Schicht (L0→L1→L2→L3) wird bottom-up je Cluster mit einem grünen Verify-Gate in Betrieb genommen, die nächste Schicht startet erst danach.

**Kritische Reihenfolge-Invarianten** (nicht umstellbar): Foundation/mgmt vor allem anderen, Registry vor abhängigen Diensten, Staging-Pilot vor Prod, stateless vor stateful je Domäne, GPU als letzte Phase nach Paritätstest, Abschaltung der Altumgebung erst nach grünem Beobachtungsfenster.

---

## 6. Durchführung (Übergangs-Playbook je Domäne)

Strangler-Fig-Muster mit graduellem Traffic-Shifting und verlustfreiem Daten-Rollback. Die Altumgebung bleibt je Domäne **Hot-Rollback**, bis das Beobachtungsfenster grün ist.

1. **Vorbereitung:** DNS-TTL der Domäne vorab auf 60 s senken (mindestens 48 h vorher). Provider-übergreifendes Mesh stellt die Konnektivität während des Parallelbetriebs her.
2. **Forward-Sync (stateful):** logische Replikation auf die neue CloudNativePG-Zielinstanz, bis der Lag nahe null ist.
3. **Stateless-Canary:** Traffic stufenweise verschieben (5 % → 25 % → 50 % → 100 %), je Stufe **Soak-Phase** mit Health-, Fehler- und Latenz-Monitoring (OpenTelemetry).
4. **Daten-Cutover:** kurzer Write-Freeze, letzte WAL anwenden, Ziel-DB zum Primary promoten.
5. **Reverse-Sync (Sicherheitsnetz):** **sofort zurück-replizieren**, solange das Beobachtungsfenster läuft, damit ein Rollback keine neuen Writes verliert.
6. **Beobachtungsfenster** (48 bis 72 h): volle Last auf der neuen Umgebung, Altumgebung als verlustfreier Rollback bereit.
7. **Freigabe:** Gate grün → Reverse-Sync stoppen, Alt-Domäne stilllegen (löschen erst, wenn endgültig sicher).

**Warum das störungsfrei ist:** Nutzer sehen keinen IP-Wechsel, Fehler werden bereits bei 5 % Traffic sichtbar (nicht bei 100 %), und der gefährlichste Schritt (Daten) ist durch Reverse-Replikation ohne Verlust umkehrbar.

**Backup-/DR durchgängig verankert:** Velero und CloudNativePG sichern über alle Wellen in unveränderliche, standortübergreifende WORM-Buckets, mit regelmäßiger Restore-Probe als Gate.

---

## 7. Tests & Validierung

Jede Welle hat ein verifizierbares Exit-Gate. Die Test-Spezifikation deckt folgende Kategorien ab:

| Bereich | Prüft |
|---|---|
| **A — HA / Resilienz** | Knoten-/Standort-Ausfall, etcd-Quorum über 3 Domänen, Replica-/Anti-Affinity-Verhalten |
| **B — Backup / DR** | Backup-Erstellung, **Restore-Probe**, Unveränderlichkeit (Object-Lock/WORM), Dual-Region |
| **C — Security (CIS, technisch)** | kube-bench, default-deny-Wirksamkeit, Policy-Enforcement, Secret-Handling |
| **D — Performance** | Latenz/Durchsatz der DB- und App-Schicht, Vergleich gegen Baseline |
| **E — Migrations-Cutover** | Daten-Cutover-Mechanik, Datenkonsistenz vor/nach Promote |
| **F — Access-Plane (Teleport)** | kurzlebige Zertifikate, Session-Audit, least-privilege-Zugriff |
| **G — Schicht-Gate (L0→L3)** | bottom-up-Gates je Cluster grün, bevor die nächste Schicht startet |
| **H — Reverse-Replikation / Canary** | **verlustfreier Rollback**, stufiges Traffic-Shifting, definierte Rollback-Kriterien |
| **I — Assistenz-Isolation** | Souveränität und Mandantentrennung des Aktions-Assistenten (A) |
| **I-B — Wissens-Assistent (B)** | permission-aware RAG, harte A↛B-Grenze (default-deny) |
| **J — LLMOps** | Eval-Gate, Guardrails, GenAI-Tracing zur Laufzeit |
| **K — GPU-Tier** | warm zu Arbeitszeiten + on-demand, Output-/Latenz-Parität gegen Baseline |

**Rollback-Kriterien (vorab definiert):** Fehlerrate oder p95-Latenz über Schwellwert, roter Datenkonsistenz-Check oder fehlgeschlagener Smoke führen zum sofortigen Traffic-Rückschwenk auf die Altumgebung (Sekunden). Da die Reverse-Replikation die Altumgebung aktuell hält, entsteht **kein Datenverlust**.

Jeder Test ist einem **Wellen-Exit-Gate** zugeordnet: Eine Welle gilt erst als abgeschlossen, wenn ihre Tests grün sind.

---

## 8. Status & Gates

- **Konzept abgeschlossen:** Architektur, Betriebskonzept, Schichten-/Zukunftsmodell, Sicherheit, Backup/DR, Kosten und Engineering-Modell sind ausgearbeitet und entscheidungsfest dokumentiert.
- **Vor produktivem Cutover (hartes Gate):** schriftliche Bestätigung von **(1) Datenresidenz Deutschland**, **(2) Auftragsverarbeitungsvertrag mit Subprozessorenliste**, **(3) aktuellem BSI-C5-Testat**. Erst danach Freigabe.
- **Nächste Schritte:** Vertrags-/Account-Voraussetzung schaffen, GPU-Quota mit Vorlauf beantragen, dann Foundation-Welle (mgmt-Cluster als Blaupause).

---

*Teil der DARC-Eigenentwicklungen. Zurück zum [Profil](../README.md).*
