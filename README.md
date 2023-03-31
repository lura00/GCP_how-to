# Getting Started with VPC Networking and Google Compute Engine

## Create a VPC network and VM instances

1. On the Navigation menu (Navigation menu icon), click VPC network > VPC networks.
2. Click Create VPC network.
3. For Name, type mynetwork.
4. For Subnet creation mode, click Automatic.
Auto mode networks create subnets in each region automatically.
5. For Firewall, select all available rules.
These are the same standard firewall rules that the default network had.
The deny-all-ingress and allow-all-egress rules are also displayed, but you cannot check or uncheck them because they are implied. These two rules have a lower Priority (higher integers indicate lower priorities) so that the allow ICMP, custom, RDP and SSH rules are considered first.
6. Click Create.
When the new network is ready, notice that a subnet was created for each region.
7. Explore the IP address range for the subnets in Lab Region and europe-west2.

# Create a VM instance in Lab Region

## Create a VM instance in the Lab Region region. Selecting a region and zone determines the subnet and assigns the internal IP address from the subnet's IP address range.

1. On the Navigation menu (Navigation menu icon), click Compute Engine > VM instances.

2. Click Create instance.

3. Specify the following, and leave the remaining settings as their defaults:

    - Property	Value (type value or select option as specified)
    - Name	mynet-us-vm
    - Region	Lab Region
    - Zone	Lab Zone
    - Series	E2
    - Machine type	e2-micro (2 vCPU, 1 GB memory)
4. Click Create.


# Explore the connectivity for VM instances
Explore the connectivity for the VM instances. Specifically, try to SSH to your VM instances using tcp:22, and ping both the internal and external IP addresses of your VM instances using ICMP. Then explore the effects of the firewall rules on connectivity by removing the firewall rules individually.

## Verify connectivity for the VM instances

The firewall rules that you created with mynetwork allow ingress SSH and ICMP traffic from within mynetwork (internal IP) and outside that network (external IP).

1. On the Navigation menu (Navigation menu icon), click Compute Engine > VM instances.
Note the external and internal IP addresses for mynet-eu-vm.
2. For mynet-us-vm, click SSH to launch a terminal and connect.
3. To test connectivity to mynet-eu-vm's internal IP, run the following command, replacing mynet-eu-vm's internal IP:

  ping -c 3 <Enter mynet-eu-vm's internal IP here>

You can ping mynet-eu-vm's internal IP because of the allow-custom firewall rule.

4. To test connectivity to mynet-eu-vm's external IP, run the following command, replacing mynet-eu-vm's external IP:

  ping -c 3 <Enter mynet-eu-vm's external IP here>
