%% Azure Hub-and-Spoke Network Architecture

graph TD
    

    HubVNET[Hub VNET]

    Firewall[Azure Firewall]
    VPN[VPN / ExpressRoute Gateway]

    HubVNET --> Firewall
    HubVNET --> VPN

    SpokeProd[Spoke VNET - Prod Workloads]
    SpokeNonProd[Spoke VNET - Non-Prod Workloads]

    HubVNET --- SpokeProd
    HubVNET --- SpokeNonProd

    %% Communication rules
    SpokeProd -. No direct access .- SpokeNonProd
