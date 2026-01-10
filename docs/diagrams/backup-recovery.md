Backup & Recovery Architecture

```mermaid
graph TD


    Workload[Workload Resources]
    Backup[Azure Backup]
    Vault[Recovery Services Vault]
    Secondary[Secondary Region]

    Workload --> Backup
    Backup --> Vault
    Vault --> Secondary
