# Checkpoint4 Submission

- **COURSE INFORMATION: CAA900ZAA.08425.2241-Capstone Project**
- **STUDENT’S NAME: Komal Sharma**
- **STUDENT'S NUMBER: 129875217**
- **GITHUB USER_ID: 129875217-myseneca**
- **TEACHER’S NAME: Atoosa Nasiri**

---

## Table of Contents
1. [Part A - Creating Network Resources using Azure CLI](#creating-network-resources-using-azure-cli)
2. [Part B - Working with Azure CLI Bash](#working-with-azure-cli-bash)
3. [Part C - Network Review Questions](#network-review-questions)
4. [Part D - Creating Virtual Machines](#creating-virtual-machines-using-azure-cli)
5. [Part E - Creating Custom Images](#creating-custom-images-from-vms-using-azure-cli)
6. [Part F - Clean Up your Environment](#clean-up-your-environment-using-azure-cli)

### Creating Network Resources using Azure CLI


1. In network_config_test.sh what does `if [[ ! $(az group list -o tsv --query "[?name=='$RG_NAME']") ]]` do? Explain your answer.
This is a conditional statement which is checking the resource group in azure using az group list and then the query is checking for a specific resource group that we have specified. This command check if the resource group exist in the azure account or not.

2. Why is it crucial to check if a resource exist before creating it? What bash syntax do you use to test this? How do you check if a `vnet` exists in vnet_create.sh?
The reason why it is important to check if any resource exist is to make sure there is no duplicate that gets created or any overwrite that happen for the resource in question. If there is any resource that already exist it might result in an error or any unexpected behaviour.We use a conditional statement to check this. if [[ $(az network vnet list -g $RG_NAME -o tsv --query "[?name=='$vnet']") ]]; is the statement we used in vnet_create.sh.

3. What is the Azure CLI command to create `vnet`? Give the specific command as per your environment and unique ID configuration. What are the required and what are the optional parameters that you need to pass to it?
az network vnet create is the CLI command used to create vnet. the command used in the script is az network vnet create -g Student-RG-1230102 --name Router-96 --location canadacentral --address-prefix 192.168.96.0/24

4. What is the Azure CLI command to create `subnet`? Give the specific command as per your environment and unique ID configuration. What are the required and what are the optional parameters that you need to pass to it?
az network vnet subnet create is the CLI command to create a subnet in the specified vnet. az network vnet subnet create --name SN1 -g Student-RG-1230102 --vnet-name Router-96 --address-prefix 192.168.96.0/24


### Working with Azure CLI Bash


1. List all VNETs using `az network vnet list` command and send the output in `json` format to `vnet_list.json`file

[vnet_list.json](bash-scripts/vnet_list.json)

2. Get the details of your `default student vnet` using `az show` command and send the output in `json` format to `student_vnet.json` files

[student_vnet.json](bash-scripts/student_vnet.json)

3. List all peerings using `az network vnet peering list` command and send the output in `table` format to `peerings.tbl`file

| AllowForwardedTraffic | AllowGatewayTransit | AllowVirtualNetworkAccess | DoNotVerifyRemoteGateways | Name                    | PeeringState | PeeringSyncLevel | ProvisioningState | ResourceGroup       | ResourceGuid                          | UseRemoteGateways |
|-----------------------|---------------------|---------------------------|---------------------------|-------------------------|--------------|------------------|-------------------|---------------------|----------------------------------------|-------------------|
| True                  | False               | True                      | False                     | Student-Bastion1230102 | Connected    | FullyInSync      | Succeeded         | Student-RG-1230102  | 7edafa6d-65f2-0a66-3b9b-c3ba1f47bac0   | False             |
| True                  | False               | True                      | False                     | StudenttoRouter         | Connected    | FullyInSync      | Succeeded         | Student-RG-1230102  | ac120069-20c5-07bf-2183-aacd48a79287   | False             |

4. Get the details of your `Router-XX` subnet `SN1` using `az show` command in `json` format and `query` it for details of subnet and rout associations. 

[router_subnet_details.json](bash-scripts/router_subnet_details.json)

5. List all routes in `RT-xx` using `az network route-table route list` command and send the output in `table` format to `route_list.tbl`file
6. Get the details of route between your `Router-xx SN1` and `Server-xx SN` using `az network route-table route show` and send the output in `json` format to `route_details.json`
7. (Optional) What CLI command will show you which subnet is associated to which route in route table? _(Hint: maybe start with 'az network vnet subnet show`)_

### Network Review Questions


1. What is Azure Virtual Network (VNET)? Elaborate in your own words, you may use diagrams if drawn by yourself.
2. In the context of Hybrid Cloud architecture. How on-prem computers can access resources inside Azure virtual network?
3. What are the most important benefits of Azure Virtual Networks? Elaborate in your own words. Do not copy/paste from Azure Documentation. Itemized list of just benefit without proper elaboration will not receive any marks
4. What is the difference between Network Security Group (NSG) and Route-Tables?
5. What is the difference between NSG and Firewalls?
6. What is a _hob-and-spoke_ network topology and how be deployed in Azure Cloud?
7. In working with Azure VNETs, do you need o to define gateways for Azure to route traffic between subnets?
8. When do you need to configure and use Virtual Network Gateways?

### Creating Virtual Machines using Azure CLI


Answer below questions for this section:

1. List all VMs and send the output in `table` format to `vm_list.tbl` file. What command did you use?
2. Get the details of your `WC-99` using `az show` command and send the output in `json` format to `WC-99-details.json` file. What command did you use?
3. List all NSG using `az list` command and send the output in `table` format to `nsg_list.tbl`file. What command did you use?
4. Provide screenshot of _auto shutdown configuration_ for `LS_XX`. Is there any command to show this? What is the time-zone? What should be the correct time settings considering the time zone differences?
5. Why `auto shutdown configuration` is not done in [vm_create](https://github.com/Azure-Project-Winter2024/Azure-Project-Scripts/blob/94d21ad5454163ae8e2ee331f8a41291fca6e155/CP4-Scripts/bash-scripts/vm_create.sh#L128) code? Why is it a separate scripts? Is it possible to configure auto shutdown at the same time you are creating the VM?

### Creating Custom Images from VMs using Azure CLI


Answer below questions for this section:

1. What are the difference between the script that creates VM from Azure Generic Image vs Custom Image? A good place to start is to compare the two scripts `custom_vm_create.sh` and `custom_vm_create.sh` and check the parameters passed to `az vm create` command. Elaborate the differences you observe.
2. If you run `custom_vm_create.sh` without custom image `version` number, the script will throw an error and show you the usage suggestion. What is the usage suggestion?
3. The script is purposefully written such that it waits on each custom image creation to be completed before proceeding to next image. Can you update the script such that custom images creation runs in background, i.e. how can you parallelize the process?_Hint: only provide the single line command that you need to update_
4. Once all custom images are successfully created, run a command in CLI that lists all your Custom Images. Change the output format to table format and embed the answer in your submission.
5. Delete your VMs using the proper script after above step is completed. Then re-create VMs using your custom images. Check is all VMs are accessible, i.e. Client VM can be reached via Bastion and Linux VMs can be accessed with ssh.
6. Get a list of your VM, NSG, NIC, Disks, and Custom Iamges using Azure CLI in table format. Which ones are empty? **Do not include screenshots, just embed the output in **table** format in your submission.

### Clean Up your Environment using Azure CLI

Answer below questions for this section:

1. After deleting list all your VMs using `az  vm list ...` with the output in `table` format. What command did you use? How can you ensure all your VMs are deleted?
2. Why you are not asked to delete Custom Images? What is the difference between VM and Custom Image that makes VM a very costly resource and Custom Images, negligible? (_Hint: It is related to OS Disk_)
3. What are cost implications of NSG or NIC? Why are you deleting them?
4. Why you are not deleting Network backend like VNET and Route-Tables?


1. Part A - Creating Network Resources using Azure CLI: Links to all files you created in this part, also embed the output of  Working with Azure CLI Bash commands that show your resource list in table format.
2. Part B -  Working with Azure CLI Bash: Links to all files you created in this part, also embed the output of  Working with Azure CLI Bash commands that show your resource list in table format.
3. Part C - Network Review Questions: Answer all the questions, include images if you need.
4. Part D - Creating Virtual Machines: Links to all files you created in this part, also embed the output of  Working with CLI Bash commands that show your resource list in table format.
5. Part E - Creating Custom Images from VMs using Azure CLI: Answer all the questions, use **ARM** (Azure Resource Manager) and include deployment `json` files in your submission. Include the property object in `json` file that shows VM image source. (Hint: will do a demo in class)
6. Part F - Clean Up your Environment using Azure CLI: Answer all the questions, use cost calculator to compare different resources and justify the resources not deleted as part of clean-up

