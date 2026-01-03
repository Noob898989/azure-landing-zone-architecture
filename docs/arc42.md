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
