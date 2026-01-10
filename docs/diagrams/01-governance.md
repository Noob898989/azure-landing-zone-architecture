# Governance – Azure Landing Zone

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
