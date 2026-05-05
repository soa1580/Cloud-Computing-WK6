# Cloud-Computing-WK6
Cloud Computing: Weekly Assignment Submission.

## 1. Created a Virtual Network named Lab-VNet-1 inside Resource Group RG-Network-Lab with address space 10.0.0.0/16. Two subnets were configured: Frontend-Subnet (10.0.1.0/24) for frontend resources and Backend-Subnet (10.0.2.0/24) for backend resources.

[img./Lab-Vnet1-Subnet]


## 2. I also deployed two virtual machines inside Lab-VNet-1. The frontend VM (front-vm) was placed in Frontend-Subnet, while the backend VM (back-vm) was placed in Backend-Subnet. Both virtual machines use Windows Server 2022, size B2ms, with RDP enabled through port 3389.

[img./front-vm.png]
[img./back-vm.png]


## 3. Connectivity test was performed by connecting to front-vm through Remote Desktop and pinging back-vm using its private IP address. The successful ping response confirms that both virtual machines can communicate internally within the same virtual network.

[img./Server-Manager.jpg]
[img./Ping-test-front-vm-to-back-vm.jpg]


## 4. Then applying the Network Security Group to the Backend-Subnet and creating a deny rule for port 3389, inbound Remote Desktop traffic to back-vm was blocked. As a result, connection attempts from front-vm to back-vm using RDP failed. This demonstrates how NSG rules can control and restrict network access within a virtual network.

[img./Lab-NSG-Deny-RDP.jpg]
[img./Lab-NSG-request-timeout.jpg]


## 5. I created a second virtual network named Lab-VNet-2 which was created with the address space 192.168.0.0/16. A subnet named VM-Subnet (192.168.1.0/24) was configured, and a virtual machine (vm-vnet2) was deployed within this subnet. The VM has a private IP address within the 192.168.1.0/24 range.

[img./Lab-VNet-2-vm-prvip.png]
[img./Lab-VNet-2-vm.png]


## 6. The virtual machines were not able to communicate. This is because they are located in different virtual networks (Lab-VNet-1 and Lab-VNet-2), and Azure does not allow communication between VNets by default. Without configuring VNet peering or another connectivity method, the networks remain isolated.

[img./Lab-VNet-1-Unlinked-Lab-VNet-2.jpg]


## 7. Virtual network peering was successfully configured between Lab-VNet-1 and Lab-VNet-2, allowing communication between resources in both networks. After peering, front-vm was able to communicate with vm-vnet2 using its private IP address, confirming successful connectivity across VNets.

[img./Lab-VNet-1-Linked-Lab-VNet-2.jpg]