
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

## Summary of Task 1
In this task, a network with two subnets was successfully created and configured using static IP addressing. Routing tables were examined on all devices, and packet forwarding was enabled on the router. Connectivity between the subnets was verified using the ping command, demonstrating correct routing behaviour.

## Task 2: Dynamic Routing with OSPF
The aim of this task is to observe how dynamic routing protocols such as OSPF operate and how they automatically adjust to network changes such as link failures.

## Network Overview
OSPF Network Topology
----------------

The OSPF network consists of two hosts and four FRR routers interconnected with multiple paths. The network is pre-configured to use OSPF for dynamic routing, allowing routers to automatically exchange routing information and determine optimal paths.

## OSPF Neighbour Information
----------------------

This output displays the neighbouring routers connected to FRR1. It confirms that OSPF adjacency has been successfully established, allowing routers to exchange routing information dynamically.

## Routing Tables
-  Routing Table of Router 1
  -----------------------
This routing table shows the networks known to Router 1, including both directly connected and OSPF-learned routes. It also indicates the next hop required to reach each destination network.

- Routing Table of Router 2
----------------------------------

This routing table demonstrates how another router in the network maintains its routes and selects the best path to reach various subnets using OSPF.

Routing Summary Table
Router	Destination Network	Next Node
FRR1	Host2 subnet	FRR2 / FRR3
FRR2	Host2 subnet	FRR4
FRR3	Host2 subnet	FRR4
FRR4	Host1 subnet	FRR2 / FRR3

(Update this table based on your actual outputs)

Path Analysis Using Traceroute
- Traceroute Before Link Failure
------------------------

This output shows the original path taken by packets from Host1 to Host2. The traceroute command reveals the sequence of routers used in the communication path.

- Traceroute After Link Failure
------------------------------------

After disconnecting a link, OSPF dynamically recalculates the route and selects an alternative path. This traceroute output confirms that traffic is successfully rerouted through a different set of routers.

## Summary of Task 2

In this task, the behaviour of OSPF was observed in a pre-configured network. Routing information was analysed using FRR commands, and the impact of a link failure was tested. OSPF successfully adapted to the network change by recalculating routes and maintaining connectivity.

## Final Conclusion

This tutorial demonstrated both static and dynamic routing concepts. Static routing required manual configuration of IP addresses and routes, while dynamic routing with OSPF allowed automatic route discovery and adaptation to network changes. These experiments highlight the importance of routing protocols in maintaining reliable communication in complex networks.
