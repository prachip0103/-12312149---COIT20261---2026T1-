
## COIT20261 – Week 05 Tutorial
VLAN Configuration using OpenvSwitch

## Task 1: Setup VLANs on Switch
The aim of this task is to configure VLANs on a managed switch using OpenvSwitch and observe how VLANs affect communication between hosts.

## Network Topology
Four Linux hosts were connected to an OpenvSwitch device using ports eth1 to eth4. Port eth0 was left unused as required.

----------------Filename: Vlan-Basics-12312149-network.png 

Network topology showing four hosts connected to the switch.

 ## IP Address Configuration
All hosts were configured within the same subnet as follows:

Host	IP Address	Subnet Mask
Host1	192.168.1.1	/24
Host2	192.168.1.2	/24
Host3	192.168.1.3	/24
Host4	192.168.1.4	/24

Commands used:

ip addr add 192.168.1.X/24 dev eth0
ip link set eth0 up
🔸 Initial Connectivity Test

Before VLAN configuration, all hosts were able to communicate with each other successfully using the ping command, confirming proper network connectivity.

 ## VLAN Configuration

Two VLANs were configured based on the student ID:

VLAN 149 → Host1 and Host2
VLAN 150 → Host3 and Host4

Commands used on the switch:

ovs-vsctl set port eth1 tag=149
ovs-vsctl set port eth2 tag=149
ovs-vsctl set port eth3 tag=150
ovs-vsctl set port eth4 tag=150
## VLAN Verification

The VLAN configuration was verified using:

ovs-vsctl show

--------------- Filename: Vlan-Basics-12312149-ports.png
 Output showing VLAN tags assigned to each switch port.

## Connectivity Test After VLAN Configuration
Communication within the same VLAN was successful:
Host1 ↔ Host2
Host3 ↔ Host4
Communication between different VLANs failed:
Host1 ↔ Host3
Host2 ↔ Host4

This demonstrates that VLANs isolate broadcast domains.

## ARP Table Observation

ARP tables were checked using:

arp -n

It was observed that hosts could only resolve MAC addresses of devices within the same VLAN.

 ## Conclusion (Task 1)

This task demonstrated how VLANs logically separate a network into multiple broadcast domains, improving network segmentation and security.

## Task 2: Setup VLANs on a Router
The aim of this task is to configure inter-VLAN routing using a Linux router and enable communication between different VLANs.

## Network Setup

The previous topology was extended by adding a Linux router connected to switch port eth0.

----------Filename: Vlan-Router-12312149-network.png
Network topology including router and switch.
## IP Address Configuration

Hosts were divided into two different subnets:

Host	VLAN	IP Address	Gateway
Host1	149	192.168.10.2	192.168.10.1
Host2	149	192.168.10.3	192.168.10.1
Host3	150	192.168.20.2	192.168.20.1
Host4	150	192.168.20.3	192.168.20.1
## Switch Configuration

Access ports:

ovs-vsctl set port eth1 tag=149
ovs-vsctl set port eth2 tag=149
ovs-vsctl set port eth3 tag=150
ovs-vsctl set port eth4 tag=150

Trunk port:

ovs-vsctl set port eth0 trunks=[]
## outer Configuration
Create VLAN sub-interfaces:
ip link add link eth0 name eth0.149 type vlan id 149
ip link add link eth0 name eth0.150 type vlan id 150
Assign IP addresses:
ip addr add 192.168.10.1/24 dev eth0.149
ip addr add 192.168.20.1/24 dev eth0.150
Enable interfaces:
ip link set eth0 up
ip link set eth0.149 up
ip link set eth0.150 up
Enable routing:
sysctl -w net.ipv4.ip_forward=1
## Connectivity Test

After router configuration:

All hosts successfully communicated across VLANs
Inter-VLAN routing worked correctly

Example:

Host1 → ping 192.168.20.2 ✅
Host3 → ping 192.168.10.2 ✅
## VLAN Verification
ovs-vsctl show
---------Filename: Vlan-Router-12312149-ports.png
 Output showing trunk port and VLAN configuration.
## Conclusion (Task 2)

This task demonstrated how a router enables communication between VLANs using sub-interfaces and IP forwarding. It highlights the concept of inter-VLAN routing in modern networks.
