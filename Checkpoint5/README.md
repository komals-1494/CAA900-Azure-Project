# Checkpoint5 Submission

- **COURSE INFORMATION: CAA900ZAA.08425.2241-Capstone Project**
- **STUDENT’S NAME: Komal Sharma**
- **STUDENT'S NUMBER: 129875217**
- **GITHUB USER_ID: 129875217-myseneca**
- **TEACHER’S NAME: Atoosa Nasiri**

---

## Table of Contents

1. [Part A - Creating & Configuring VMs - Using Portal](#creating--configuring-vms---using-portal)
2. [Part B - Enable IP_Forwarding - Using Portal](#enable-ip_forwarding---using-portal)
3. [Part C - Basic Connectivity - VM Configuration](#basic-connectivity---vm-configuration)
4. [Part D - Creating & Configuring VM Images - Using Portal](#creating--configuring-vm-images---using-portal)
5. [Part E - Azure Cost Analysis Charts](#azure-cost-analysis-charts)
6. [Part F - Create Customized Azure Dashboard](#create-customized-azure-dashboard)

### Creating & Configuring VMs - Using Portal

1. What is the difference between Windows machine NSG and Linux machine NSG rules? Why? Do you need a rule for ssh or rdp? What happens if you delete specific ssh and rdp rules?

Difference Between Windows and Linux NSG Rules:
Windows computers use RDP to connect remotely. It uses a port, numbered 3389.
Linux computers use SSH for remote connections. Its port number is 22.

What Happens if we Delete SSH or RDP Rules:

If we delete SSH rules from a Linux setup, people won't be able to remotely connect to that Linux computer.
If we delete RDP rules from a Windows setup, people won't be able to remotely connect to that Windows computer.

2. Work from Azure Bash CLI in Portal to get a list of your VM, NSG, NIC, and Disks.

# Azure CLI Commands Used:

```bash
az group list --output table
az vm list -g $RG --output table
az network nic list -g $RG --output table
az network nsg list -g $RG --output table
az disk list -g $RG --output table
```
Output for each of the command:

# Resource Group Overview

## Resource Groups

| Name                | Location       | Status    |
|---------------------|----------------|-----------|
| Bastion_RG          | canadacentral | Succeeded |
| NetworkWatcherRG    | canadacentral | Succeeded |
| Student-RG-1230102  | canadacentral | Succeeded |

## Virtual Machines

| Name | Resource Group      | Location       | Zones |
|------|---------------------|----------------|-------|
| LR-96 | Student-RG-1230102 | canadacentral | 1     |
| LS-96 | Student-RG-1230102 | canadacentral | 1     |
| WC-96 | Student-RG-1230102 | canadacentral | 1     |
| WS-96 | Student-RG-1230102 | canadacentral | 1     |

## Network Interfaces

| AuxiliaryMode | AuxiliarySku | DisableTcpStateTracking | EnableAcceleratedNetworking | EnableIPForwarding | Location       | MacAddress        | Name       | NicType  | Primary | ProvisioningState | ResourceGroup      | ResourceGuid                         | VnetEncryptionSupported |
|---------------|--------------|--------------------------|-----------------------------|--------------------|----------------|-------------------|------------|----------|---------|-------------------|-------------------|--------------------------------------|-------------------------|
| None          | None         | False                    | False                       | False              | canadacentral | 00-0D-3A-84-89-DB | lr-96981_z1 | Standard | True    | Succeeded         | Student-RG-1230102 | 056137e3-6c55-4ef2-8c13-5e31cdb02d27 | False                   |
| None          | None         | False                    | False                       | False              | canadacentral | 60-45-BD-61-23-AE | ls-9657_z1  | Standard | True    | Succeeded         | Student-RG-1230102 | 4d637045-b62d-4785-90cd-0e1535384824 | False                   |
| None          | None         | False                    | False                       | False              | canadacentral | 60-45-BD-5F-CE-16 | wc-96521_z1 | Standard | True    | Succeeded         | Student-RG-1230102 | b564b42a-ffa9-41e3-b01f-761c69d744be | False                   |
| None          | None         | False                    | False                       | False              | canadacentral | 60-45-BD-5B-C6-22 | ws-96706_z1 | Standard | True    | Succeeded         | Student-RG-1230102 | 21d8632f-bb83-4c08-a4af-aefb7e4d27d2 | False                   |

## Network Security Groups

| Location       | Name       | ProvisioningState | ResourceGroup      | ResourceGuid                          |
|----------------|------------|-------------------|-------------------|---------------------------------------|
| canadacentral | LR-96-nsg  | Succeeded         | Student-RG-1230102 | 2f7f42c7-5961-455e-bf3f-82afcaf57ce0  |
| canadacentral | LS-96-nsg  | Succeeded         | Student-RG-1230102 | ae31bb78-8a29-4136-bbfc-4332bd978424  |
| canadacentral | WC-96-nsg  | Succeeded         | Student-RG-1230102 | 4434ae83-d0a7-4bae-b23f-ea1ccd3cc045  |
| canadacentral | WS-96-nsg  | Succeeded         | Student-RG-1230102 | 4b5cb5fc-7503-4ce7-ab59-71dc0d3295cb  |

## Disks

| Name                                             | ResourceGroup      | Location       | Zones | Sku           | OsType | SizeGb | ProvisioningState |
|--------------------------------------------------|-------------------|----------------|-------|---------------|--------|--------|-------------------|
| LR-96_OsDisk_1_dfe94783567d47de84cf51793a21af97  | Student-RG-1230102 | canadacentral | 1     | Standard_LRS  | Linux  | 64     | Succeeded         |
| LS-96_OsDisk_1_6ac385e4df964ab8a964380ee14861f0  | Student-RG-1230102 | canadacentral | 1     | Standard_LRS  | Linux  | 64     | Succeeded         |
| WC-96_OsDisk_1_cd1c2fcb257d4a3fb83a0ec82d2c28f4  | Student-RG-1230102 | canadacentral | 1     | Standard_LRS  | Windows| 127    | Succeeded         |
| WS-96_OsDisk_1_829b141d55d347a89078fc245b4b4265  | Student-RG-1230102 | canadacentral | 1     | Standard_LRS  | Windows| 127    | Succeeded         |


### Enable IP_Forwarding - Using Portal

1. Check the status of ip-forwarding using the command az network nic ip-config show with output format as json. 

```bash
az network nic show --resource-group $RG --name lr-96981_z1 --query "enableIpForwarding" --output json
```
2. When your output format is json, which property shows the status of the ip-forwarding attribute?

"enableIPForwarding": true,

3. Check if the IP forwarding in NIC is enabled using Azure bash. 

```bash

az network nic show --resource-group $RG --name lr-96981_z1 --query "enableIPForwarding"

```

### Basic Connectivity - VM Configuration
### Creating & Configuring VM Images - Using Portal
### Azure Cost Analysis Charts
### Create Customized Azure Dashboard