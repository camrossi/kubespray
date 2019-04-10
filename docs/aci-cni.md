ACI CNI
======

## Host Pre Requisites:

* Ubuntu Linux 16 or 18 
* The interface that connects to ACI has MTU of at least 1600
* ACI is the default GW of the host 


## How to Configure ACI CNI:

* Enabled the ACI CNI plugin by setting editing the inventory/group_vars/k8s-cluster/k8s-cluster.yml file:
 
 ``` kube_network_plugin: aci-cni ```
 
* Generate the ACI CNI configuration file with acc-provision, for details refer to the [ACI CNI configuration guide](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/aci/apic/sw/kb/b_Kubernetes_Integration_with_ACI.html) and copy the file to your master. Edit inventory/group_vars/k8s-cluster/k8s-net-aci-cni.yaml to point to the location of the ACI CNI file on the master:


 ``` aci_cni_config_file: <path/aci_cni_config>```


## Node DHCP Configuration for OpFlex
As part of this ansible playbook the DHCP configuration for OpFlex is automated. The playbook will look up the interface mac address based on the ip address where you bind your kube-api.
