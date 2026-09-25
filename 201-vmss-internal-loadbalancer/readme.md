
# Deployment of a VM Scale Set of Linux VMs behind an internal load balancer

This directory contains a corrected version of Microsoft's [201-vmss-internal-loadbalancer](https://github.com/Azure/azure-quickstart-templates/tree/master/201-vmss-internal-loadbalancer) Azure Quick Start template. The original template was copied to the [AZ900-ARMTemplates repository](https://github.com/Stowarzyszenie-Horyzont-Wiedzy/AZ900-ARMTemplates/tree/main/201-vmss-internal-loadbalancer), but it did not work correctly in the Skillable AZ-900 lab **Enable Azure Virtual Machine Scale Sets for High Availability and Scalability (Guided)**. This version contains the changes needed for that lab.

The template deploys a Linux Virtual Machine Scale Set behind an internal load balancer and includes a jump box for SSH access to the VM instances.




[![Deploy To Azure](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazure.svg?sanitize=true)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FStowarzyszenie-Horyzont-Wiedzy%2FAZ900-ARMTemplates%2Fmain%2F201-vmss-internal-loadbalancer%2Fazuredeploy.json)  [![Visualize](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/visualizebutton.svg?sanitize=true)](http://armviz.io/#/?load=https://raw.githubusercontent.com/Stowarzyszenie-Horyzont-Wiedzy/AZ900-ARMTemplates/main/201-vmss-internal-loadbalancer/azuredeploy.json)

This template allows you to deploy a VM Scale Set of Linux VMs using Ubuntu Linux. Because the load balancer is internal, you must first SSH into the jump box, then SSH from there into a specific VM behind the load balancer. To connect to a VM in the scale set, open the load balancer in the Azure portal, find its NAT rules, and use the required rule. For example, if there is a NAT rule on port 50000, run the following command from the jump box:

ssh -p 50000 {username}@{public-ip-address}

PARAMETER RESTRICTIONS
======================

* `vmssName` must be 3-61 characters in length. It should also be globally unique across Azure.
* `instanceCount` must be **4** or less. The value in `azuredeploy.parameters.json` must be changed if necessary before deployment.

