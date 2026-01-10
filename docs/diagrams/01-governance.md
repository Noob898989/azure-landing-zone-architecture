```mermaid
graph TD
  ...

👉 **ALLES danach ist wieder normales Markdown**

---

## 🔧 SO FIXT DU ES JETZT (1-Minute-Fix)

### ✅ **KORRIGIERTE VERSION – BITTE 1:1 ÜBERNEHMEN**

```markdown
# Governance – Azure Landing Zone

Dieses Diagramm zeigt die Governance-Struktur der Azure Landing Zone
auf Basis von Management Groups und Subscriptions.

```mermaid
graph TD
    Tenant[Azure Tenant / Entra ID]

    RootMG[Tenant Root Group]

    PlatformMG[Platform Management Group]
    WorkloadMG[Landing Zone Management Group]

    MgmtSub[Management Subscription]
    ConnSub[Connectivity Subscription]

    ProdSub[Workload Subscription - Prod]
    NonProdSub[Workload Subscription - Non-Prod]

    Tenant --> RootMG
    RootMG --> PlatformMG
    RootMG --> WorkloadMG

    PlatformMG --> MgmtSub
    PlatformMG --> ConnSub

    WorkloadMG --> ProdSub
    WorkloadMG --> NonProdSub

---

## ⚠️ ZWEI WICHTIGE MERMAID-REGELN (MERKEN!)

### 1️⃣ **Keine Sonderzeichen**
❌ `–` (Gedankenstrich)  
❌ `**`  
❌ Emojis  

👉 Verwende:

### 2️⃣ **Markdown-Überschriften NIE im Mermaid-Block**
Alles was mit `#` beginnt → **außerhalb** des Diagramms.

---

## ✅ WENN ES JETZT SICHTBAR IST …

Dann hast du:

✔ GitHub-fähige Architekturdiagramme  
✔ IaC-Denke für Architektur  
✔ Interview-taugliche Artefakte  
✔ Senior-Level Vorgehen

---

## 🔥 NÄCHSTER SCHRITT (ich bin bereit)

👉 Antworte mit **einem** der folgenden Wörter:

- **„Governance-Diagramm sichtbar“**
- **„Noch Fehler“**

Danach machen wir **Netzwerk Hub-&-Spoke** (noch besser 😎).
