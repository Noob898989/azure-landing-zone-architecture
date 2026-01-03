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
