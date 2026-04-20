## COIT20261 – Week 06 Tutorial Submission
Prachi Devidkumar Patel
12312149

## Task 1: ARP
This screenshot shows the ARP table of Host A before any communication occurs. The ip neigh show command is used to display the ARP cache, which stores mappings between IP addresses and MAC addresses. At this stage, the table is empty because no packets have been transmitted to other devices. This demonstrates that ARP entries are not pre-configured but are dynamically learned only when communication is initiated.

## Initial ARP Table
The ARP table is initially empty before communication
---------
## IP Configuration
-----------
These screenshots confirm that Host1 and Host2 are configured within the same subnet (10.10.1.0/24). Both interfaces are in the UP state, meaning they are active and capable of sending and receiving packets. Since both hosts share the same subnet, communication between them occurs directly without requiring a router. This setup is essential for ARP operation, as ARP is used only within a local network.
--------
These screenshots show that Host3 and Host4 are configured in a different subnet (10.10.2.0/24). This separation of subnets introduces the need for routing when communicating with devices in other networks. ARP will still function within this subnet, but inter-subnet communication will require routers.

ARP works by broadcasting a request such as:
"Who has IP address X?"

The device with that IP responds with its MAC address. This mapping is then stored in the ARP table for future communication. Over time, unused entries may expire, ensuring the table remains up to date.
The experiment demonstrates that ARP dynamically resolves IP addresses into MAC addresses only when communication occurs. Initially, no entries are present, but once hosts interact, the ARP table is populated with reachable devices. This confirms that ARP operates automatically in the background to support data transmission within a LAN.

## Task 2: Routing and Default Gateway
---------network
This screenshot illustrates a multi-subnet network topology implemented in GNS3. The network is divided into three logical segments:

A local subnet for Host1 and Host2
A second subnet for Host3 and Host4
A dedicated link between Router1 and Router2

Switches are used to connect hosts within the same subnet, while routers are responsible for forwarding traffic between different subnets. This design reflects a real-world hierarchical network structure.
## Host1 to Router1 Ping
-------router1ping
This screenshot shows a successful ICMP ping from Host1 to Router1. The response confirms that Layer 2 (data link layer) and Layer 3 (network layer) connectivity are functioning correctly within the same subnet. It also indicates that ARP has successfully resolved the MAC address of the router, enabling packet delivery.
## Router-to-Router Communication

This screenshot demonstrates successful communication between Router1 and Router2 over the interconnecting subnet (192.168.12.0/24). This confirms that both routers are correctly configured with IP addresses and that the physical and logical link between them is operational. This step is critical because routers must communicate with each other to forward traffic between different networks.

The network successfully enabled communication across multiple subnets using static routing. Hosts were configured with default gateways, and routers were configured to forward packets between networks. The successful ping results demonstrate that routing tables were correctly implemented and that end-to-end connectivity was achieved.

## CONCLUSION
This lab provided a practical understanding of how ARP and routing operate within a network. ARP was shown to dynamically resolve IP addresses into MAC addresses within a local subnet, while routing enabled communication across multiple subnets. The successful configuration of IP addressing, default gateways, and static routes demonstrates a functional and correctly designed network. These concepts are essential for real-world networking and form the foundation of modern communication systems.
