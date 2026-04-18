
## Week 04 Tutorial Report
- Student Name: Prachi Patel
- Student ID: 12312149
- Unit: COIT20261

## Task 1: View Routing Tables
- The aim of this task is to understand how routing tables operate in a network and how packet forwarding is enabled on a router. This involves configuring static IP addresses, enabling/disabling forwarding, and verifying connectivity between different subnets

## Network Design
![Network](./images/week04/View-Routes-12312149-network.png)

- This network consists of three Linux hosts, one Linux router, and one Ethernet switch. Host1 and Host2 are connected to the switch along with the router’s first interface (eth0), forming the first subnet (10.1.1.0/24). Host3 is connected directly to the router’s second interface (eth1), forming the second subnet (10.1.2.0/24). This setup enables communication between two different subnets through the router.

## IP Configuration and Routing Tables

![Route host1](./images/week04/view_route_host1.png)

![ipForward1](./images/week04/ipForward_host1.png)

![Route host2](./images/week04/view_route_host2.png)

![ipForward2](./images/week04/ipForward_host2.png)

![Route host3](./images/week04/view_route_host3.png)

![ipForward3](./images/week04/ipForward_host3.png)

![Route Router](./images/week04/ip_route_router.png)

![Ipforward Router](./images/week04/ipForward_router.png)


The IP configuration shows that each host is assigned a static IP address within its respective subnet. The router has two interfaces configured for both subnets. Forwarding is disabled on all hosts (ip_forward = 0) and enabled on the router (ip_forward = 1). Each host contains a default route pointing to the router, while the router maintains routes for both connected subnets.

## Connectivity Test
![Ping](./images/week04/View-Routes-12312149-ping.png)

This figure demonstrates successful communication between hosts located in different subnets. The ping results confirm that the router is correctly forwarding packets between the two networks, indicating that the routing configuration is functioning as expected.

##Summary of Task 1
In this task, a network with two subnets was successfully created and configured using static IP addressing. Routing tables were examined on all devices, and packet forwarding was enabled on the router. Connectivity between the subnets was verified using the ping command, demonstrating correct routing behaviour.
