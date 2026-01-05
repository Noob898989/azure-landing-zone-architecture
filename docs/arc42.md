# arc42 – Azure Landing Zone Architecture


## 1. Kontext und Scope

### Business Context
Diese Architektur beschreibt eine standardisierte Azure Landing Zone als Grundlage für eine sichere und regelkonforme Cloud-Nutzung in Enterprise- und Public-Sector-Umgebungen.

Die Landing Zone ermöglicht:
- Eine kontrollierte Einführung von Cloud-Workloads
- Klare Trennung von Verantwortlichkeiten
- Zentrale Durchsetzung von Governance- und Security-Vorgaben

### Technical Context
Die Architektur basiert auf Microsoft Azure und fokussiert sich auf folgende Kernkomponenten:
- Entra ID (Identity and Access Management)
- Azure Management Groups und Subscriptions
- Azure Policy und Role-Based Access Control (RBAC)
- Zentrales Logging und Monitoring

### Out of Scope
Nicht Bestandteil dieser Architektur sind:
- Applikationsspezifische Architekturen
- Konkrete Workload-Implementierungen
- CI/CD- oder Deployment-Pipelines


## 2. Qualitätsziele

Die folgenden Qualitätsziele leiten alle Architekturentscheidungen:

### Security
- Durchsetzung des Least Privilege Principle mittels RBAC
- Zentrale Identitätsverwaltung über Entra ID
- Policy-basierte Sicherheitskontrollen auf Subscription-Ebene

### Compliance und Governance
- Durchsetzung von Policies gemäß regulatorischer Anforderungen
- Klare Strukturierung von Management Groups und Subscriptions
- Nachvollziehbare und auditierbare Konfigurationen

### Maintainability
- Standardisierte und dokumentierte Architektur-Patterns
- Klare Zuständigkeiten und Rollenmodelle
- Reduzierte operative Komplexität

### Cost Transparency
- Vorhersehbare Kosten durch Subscription-Grenzen
- Monitoring und Alerts für Kostenabweichungen
- Vermeidung unkontrollierter Ressourcenerstellung

## 3. Stakeholder und Rollen

### Business Stakeholder
Vertreter der Fachbereiche, die Cloud-Services nutzen, um fachliche Anforderungen umzusetzen.

**Interessen:**
- Schnelle Bereitstellung von Cloud-Services
- Hohe Verfügbarkeit und Zuverlässigkeit
- Transparente Kosten

---

### Cloud Governance Team
Zentrales Team zur Definition und Durchsetzung von Governance-, Security- und Compliance-Vorgaben.

**Verantwortlichkeiten:**
- Definition von Azure Policies
- Verwaltung von Management Groups und Subscriptions
- Überwachung der Einhaltung von Compliance-Anforderungen

---

### Cloud Platform Team
Technisches Team, das die Azure Landing Zone bereitstellt und betreibt.

**Verantwortlichkeiten:**
- Umsetzung der Architekturvorgaben
- Betrieb von zentralen Plattform-Services
- Incident- und Change-Management

---

### Workload Teams
Applikations- oder Projektteams, die Workloads innerhalb der Landing Zone betreiben.

**Verantwortlichkeiten:**
- Umsetzung applikationsspezifischer Anforderungen
- Betrieb der eigenen Ressourcen innerhalb der Subscriptions
- Einhaltung der definierten Policies und Security-Vorgaben

---

### Cloud Solution Architect
Rolle mit übergreifender Architekturverantwortung.

**Verantwortlichkeiten:**
- Definition und Weiterentwicklung der Cloud-Architektur
- Bewertung von Architekturentscheidungen
- Abstimmung zwischen Business- und Technik-Stakeholdern
- Sicherstellung der Einhaltung der Qualitätsziele

## 4. Lösungsstrategie

Die Lösungsstrategie definiert die grundlegenden Architekturprinzipien und Leitplanken für die Azure Landing Zone.

### Architekturprinzipien

- **Security by Design**  
  Security-Anforderungen werden von Beginn an in die Architektur integriert und nicht nachträglich ergänzt.

- **Least Privilege Principle**  
  Zugriffsrechte werden strikt auf das notwendige Minimum beschränkt.

- **Policy-driven Governance**  
  Governance- und Compliance-Anforderungen werden technisch über Azure Policy durchgesetzt.

- **Separation of Concerns**  
  Trennung von Plattform-, Governance- und Workload-Verantwortlichkeiten.

- **Standardization over Customization**  
  Bevorzugung standardisierter Azure-Services und Architektur-Patterns.

---

### Technologie-Strategie

Die Architektur basiert bewusst auf nativen Azure-Services:

- Identity & Access: Entra ID
- Governance: Azure Management Groups, Azure Policy, RBAC
- Monitoring: Azure Monitor, Log Analytics
- Networking: Azure Virtual Network, Network Security Groups

Der Einsatz zusätzlicher Plattformen oder Drittanbieter-Lösungen wird nur nach Architektur-Review bewertet.

---

### Excluded Technologies and Patterns

Folgende Ansätze sind bewusst ausgeschlossen:

- Individuelle Berechtigungsmodelle außerhalb von RBAC
- Direkte Ressourcenerstellung ohne Policy-Validierung
- Unkontrollierte Subscription-Erstellung
- Workloads ohne zentrale Monitoring-Anbindung

## 5. Bausteinsicht (Building Block View)

Die Bausteinsicht beschreibt die strukturellen Hauptkomponenten der Azure Landing Zone sowie deren Verantwortlichkeiten.

### Level 1 – Systemübersicht

Die Azure Landing Zone besteht aus folgenden Hauptbausteinen:

- **Tenant Root Group**  
  Oberste Management Group zur Durchsetzung globaler Policies.

- **Platform Management Group**  
  Management Group für zentrale Plattform-Services wie Identity, Networking und Monitoring.

- **Landing Zone Management Group**  
  Management Group für produktive und nicht-produktive Workload-Subscriptions.

- **Connectivity Subscription**  
  Zentrale Subscription für Netzwerk-Services (z. B. Virtual Networks, VPN, ExpressRoute).

- **Management Subscription**  
  Zentrale Subscription für Monitoring, Logging und Security-Services.

- **Workload Subscriptions**  
  Subscriptions für Applikations- und Fachbereichs-Workloads mit klarer Kosten- und Verantwortlichkeitstrennung.

---

### Level 2 – Plattform-Bausteine

#### Identity & Access
- Zentrale Identitätsverwaltung über Entra ID
- Zugriffskontrolle mittels RBAC
- Trennung von administrativen und operativen Rollen

#### Governance
- Strukturierung über Management Groups
- Durchsetzung von Azure Policy
- Zentrale Richtlinien für Security und Compliance

#### Networking
- Hub-and-Spoke Netzwerk-Topologie
- Zentrale Netzwerk-Services in der Connectivity Subscription
- Kontrollierte Anbindung von Workload-Spokes

#### Monitoring & Logging
- Zentrale Erfassung von Logs und Metriken
- Nutzung von Azure Monitor und Log Analytics
- Zentrale Auswertung sicherheitsrelevanter Ereignisse

## 6. Laufzeitsicht (Runtime View)

Die Laufzeitsicht beschreibt typische Abläufe und Interaktionen innerhalb der Azure Landing Zone.

### 6.1 Erstellung einer neuen Workload Subscription

1. Ein Workload Team beantragt eine neue Subscription.
2. Das Cloud Governance Team prüft den Antrag auf Compliance- und Security-Anforderungen.
3. Die Subscription wird der passenden Management Group zugeordnet.
4. Vordefinierte Azure Policies und RBAC-Rollen werden automatisch angewendet.
5. Die Subscription wird an zentrale Monitoring- und Logging-Services angebunden.
6. Das Workload Team kann innerhalb der definierten Leitplanken Ressourcen bereitstellen.

---

### 6.2 Bereitstellung eines neuen Workloads

1. Das Workload Team plant die Bereitstellung eines neuen Workloads.
2. Governance- und Security-Policies validieren die Konfiguration.
3. Ressourcen werden innerhalb der genehmigten Subscription erstellt.
4. Monitoring, Logging und Security Alerts werden automatisch aktiviert.
5. Der Betrieb erfolgt gemäß den definierten Qualitätszielen.

---

### 6.3 Policy-Verletzungen und Governance-Eskalation

1. Eine Azure Policy erkennt eine nicht-konforme Ressource.
2. Die Erstellung wird blockiert oder als non-compliant markiert.
3. Das Cloud Governance Team wird informiert.
4. Korrekturmaßnahmen werden eingeleitet.
5. Die Konformität wird erneut überprüft.

## 7. Verteilungssicht (Deployment View)

Die Verteilungssicht beschreibt die logische und physische Platzierung der Architekturbausteine innerhalb von Microsoft Azure.

### Regionen
- Zentrale Plattform-Services werden in einer primären Azure Region betrieben.
- Kritische Services können optional in einer sekundären Region für High Availability vorgesehen werden.
- Die Auswahl der Regionen erfolgt unter Berücksichtigung von Data Residency und Compliance-Anforderungen.

---

### Management Groups und Subscriptions
- Die Tenant Root Group bildet die oberste Governance-Ebene.
- Platform Management Groups enthalten zentrale Subscriptions für Management und Connectivity.
- Workload Management Groups trennen produktive und nicht-produktive Subscriptions.
- Jede Subscription ist genau einer Management Group zugeordnet.

---

### Netzwerkverteilung
- Einsatz einer Hub-and-Spoke Netzwerk-Topologie.
- Zentrale Netzwerk-Services (z. B. Firewall, VPN, ExpressRoute) befinden sich im Hub.
- Workload-Spokes sind logisch getrennt und nur kontrolliert mit dem Hub verbunden.

---

### Monitoring und Logging
- Zentrale Log Analytics Workspace in der Management Subscription.
- Alle Subscriptions senden Logs und Metriken zentral ein.
- Regionale Ausfälle beeinträchtigen nicht die Governance- und Monitoring-Struktur.

## 8. Querschnittliche Konzepte

### Identity & Access Management
- Zentrale Identitätsverwaltung über Entra ID
- Zugriffskontrolle über Role-Based Access Control (RBAC)
- Trennung von administrativen, operativen und lesenden Rollen
- Nutzung von Privileged Identity Management (PIM) für erhöhte Rechte

---

### Security
- Security by Design als Grundprinzip
- Durchsetzung von Sicherheitsrichtlinien über Azure Policy
- Zentrale Überwachung sicherheitsrelevanter Ereignisse
- Nutzung von Microsoft Defender for Cloud

---

### Governance & Compliance
- Einheitliche Governance-Vorgaben über Management Groups
- Policy-basierte Kontrolle aller Subscriptions
- Regelmäßige Überprüfung der Compliance-Reports
- Dokumentierte Ausnahmeprozesse (Policy Exemptions)

---

### Monitoring & Logging
- Zentrales Monitoring über Azure Monitor
- Zentrale Log-Erfassung in Log Analytics
- Standardisierte Alerts für Security- und Betriebsereignisse
- Klare Verantwortlichkeiten für Alert-Reaktionen

---

### Cost Management
- Zentrale Kostenüberwachung über Azure Cost Management
- Nutzung von Tags zur Kostenverteilung
- Budget-Definitionen mit Alerting
- Regelmäßige Kosten-Reviews mit Workload Teams

---

### Backup & Recovery
- Definition zentraler Backup-Standards
- Nutzung nativer Azure Backup Services
- Klare Recovery-Ziele (RPO / RTO) je Workload
- Regelmäßige Wiederherstellungstests

Kapitel 9 – Architekturentscheidungen (finale Struktur)

## 9. Architekturentscheidungen

Die folgenden Architekturentscheidungen dokumentieren zentrale, nicht triviale Entscheidungen der Azure Landing Zone Architektur.
Sie dienen der Nachvollziehbarkeit, Wiederverwendbarkeit und Auditierbarkeit der Architektur.

Alle Entscheidungen wurden unter Berücksichtigung der definierten Qualitätsziele sowie regulatorischer und organisatorischer Anforderungen getroffen.

9.1 Übersicht der Architekturentscheidungen

### 9.1 Übersicht der Architekturentscheidungen

| ADR-ID  | Titel |                                         
ADR-001 Zentrale Identität Entra ID
ADR-002: Policy-driven Governance über Azure Policy
ADR-003: Separation of Concerns
ADR-004: Subscription- & Management-Group-Struktur
ADR-005: Zentrales Monitoring & Logging
ADR-006: Cost Governance & Cost Transparency
ADR-009: Zentrales Logging & Monitoring
ADR-007-network-segmentation.md
ADR-008-backup-disaster-recovery.md
ADR-010-workload-isolation-by-criticality.md

9.2 Referenzierung der ADRs

### 9.2 Detaillierte Architekturentscheidungen

Die detaillierte Beschreibung der einzelnen Architekturentscheidungen ist in separaten Architecture Decision Records (ADR) dokumentiert.

Die ADRs befinden sich im Verzeichnis:

/docs/ADR/

