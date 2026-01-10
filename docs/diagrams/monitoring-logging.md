Monitoring & Logging Architecture

```mermaid
graph TD
  

    AzureMonitor[Azure Monitor]
    LogAnalytics[Central Log Analytics Workspace]

    MgmtSub[Management Subscription]
    WorkloadSubs[Workload Subscriptions]
    Resources[Azure Resources]

    Resources --> AzureMonitor
    AzureMonitor --> LogAnalytics

    WorkloadSubs --> LogAnalytics
    MgmtSub --> LogAnalytics
