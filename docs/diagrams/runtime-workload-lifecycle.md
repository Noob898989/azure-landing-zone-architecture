Workload Lifecycle

```mermaid
sequenceDiagram
 

    participant WT as Workload Team
    participant CG as Cloud Governance Team
    participant AZ as Azure Platform

    WT->>CG: Request new Subscription
    CG->>AZ: Validate Governance & Security
    AZ->>AZ: Apply Policies & RBAC
    AZ->>AZ: Attach Monitoring
    AZ->>WT: Subscription ready
