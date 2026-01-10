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

    ProdSub[Workload Subscription – Prod]
    NonProdSub[Workload Subscription – Non-Prod]

    Tenant --> RootMG
    RootMG --> PlatformMG
    RootMG --> WorkloadMG

    PlatformMG --> MgmtSub
    PlatformMG --> ConnSub
    WorkloadMG --> ProdSub
    WorkloadMG --> NonProdSub

---

## **SCHRITT 4 – Commit & Push (3 Minuten)**

- Commit Message:

- Push nach GitHub

👉 Öffne die Datei im Browser  
👉 **Diagramm MUSS sichtbar sein**

Wenn ja: ✅ **alles richtig gemacht**

---

# 🧠 WARUM DAS GENAU DAS RICHTIGE IST

Du hast jetzt:

✔ Architektur **visualisiert**  
✔ Diagramm **versionierbar**  
✔ **Keine PowerPoint-Hölle**  
✔ **Interview-tauglich**  
✔ **Architekturstil auf Senior-Level**

Das ist exakt das, was Cloud-Architekten tun.

---

# 🔥 SCHRITT 5 – DANACH (sag mir dann einfach „weiter“)  

Dann machen wir **nacheinander**:

### 2️⃣ Netzwerk Hub & Spoke  
