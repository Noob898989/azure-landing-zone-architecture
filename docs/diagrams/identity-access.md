Identity & Access Architecture


graph TD
  
    EntraID[Entra ID Tenant]

    Users[Users]
    Groups[Security Groups]
    Roles[RBAC Roles]

    ManagementGroup[Management Group]
    Subscription[Subscription]
    Resources[Azure Resources]

    EntraID --> Users
    EntraID --> Groups
    Users --> Groups
    Groups --> Roles
    Roles --> ManagementGroup
    ManagementGroup --> Subscription
    Subscription --> Resources
