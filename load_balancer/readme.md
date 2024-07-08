# Load Balancer

## Use Case
The diagram indicates the output, we need to achieve:
<img width="1187" alt="Screenshot 2024-07-08 at 7 37 06 PM" src="https://github.com/sidsri1999/az-training/assets/61539851/4eecc904-985d-46dc-8086-fbd3ff298a10">


## Steps

### Create a resource group
<img width="477" alt="Screenshot 2024-07-04 at 11 58 15 PM" src="https://github.com/sidsri1999/az-training/assets/61539851/e137526b-9c10-41d9-a106-d4535b214df5">

### Create a virtual network
<img width="516" alt="Screenshot 2024-07-05 at 12 04 30 AM" src="https://github.com/sidsri1999/az-training/assets/61539851/1888efbe-d2d3-44cf-9845-7a71c742f64f">

### Create First Virtual Machine
1. Resource group: rg-contoso-06
2. Virtual machine name: vm-win-01
3. Region: West US
4. Availability Options: Availability Set
5. Availability Set:
   - Create new availibility set
   - <img width="574" alt="Screenshot 2024-07-05 at 12 18 28 AM" src="https://github.com/sidsri1999/az-training/assets/61539851/00400f6b-6b55-4173-a2ad-8a405aace61b">
6. Image: Windows Server 2022 Datacenter: Azure Edition - x64 Gen2
7. Size: Standard_B2ms - 2 vcpus, 8 GiB memory
8. Provide username and password.
9. Choose default params in disks.
10. For networking:
    - Virtual network: vnet-contoso
    - Subnet: default (10.0.0.0/24)
    - Public IP: pip-vm-win-01
    - NIC network security group: Advanced (We are going to make nsg same for both VMs).
    - Configure network security group: Create New
        - name: nsg-contoso
        - Add an inbound rule:
            -  Service: http
            -  <img width="575" alt="Screenshot 2024-07-05 at 12 30 16 AM" src="https://github.com/sidsri1999/az-training/assets/61539851/848cb915-790b-41a7-bf77-b268638fe1c1">
11. https://github.com/sidsri1999/az-training/assets/61539851/82bb4976-1d19-4db6-9dbf-8583543dc43e

### Create Second Virtual Machine
1. Resource group: rg-contoso-06
2. Virtual machine name: vm-win-02
3. Region: West US
4. Availability Options: Availability Set
5. Availability Set: as-contoso (Use the exisiting 1, created for vm-win-01)
6. Image: Windows Server 2022 Datacenter: Azure Edition - x64 Gen2
7. Size: Standard_B2ms - 2 vcpus, 8 GiB memory
8. Provide username and password.
9. Choose default params in disks.
10. For networking:
    - Virtual network: vnet-contoso
    - Subnet: default (10.0.0.0/24)
    - Public IP: pip-vm-win-02
    - NIC network security group: Advanced
    - Configure network security group: nsg-contoso (use existing,created during vm-win-01 creation)
11. https://github.com/sidsri1999/az-training/assets/61539851/3e9d5789-1541-45cf-a8fb-dfab565c8bba

### Create Load Balancer






