# Task 1: Setup VLANs on Switch

## Aim

To configure VLANs on an OpenvSwitch and verify communication behavior between hosts in same and different VLANs.
### Network Setup

* 4 Linux Hosts connected to OpenvSwitch
* Host1 → eth1
* Host2 → eth2
* Host3 → eth3
* Host4 → eth4

---

### IP Configuration

All hosts were configured in same subnet (192.168.10.0/24).

---

### VLAN Configuration

* VLAN 149 → Host1, Host2
* VLAN 150 → Host3, Host4

---

### Testing

* Same VLAN → SUCCESS
* Different VLAN → FAILED

---

## Screenshots (Task 1)

### 1. Network Topology

[INSERT IMAGE: Vlan-Basics-12312149-network.png]

**Description:**
This screenshot shows the GNS3 topology with four Linux hosts connected to the OpenvSwitch. Each host is connected to ports eth1 to eth4, forming the base network structure.

---

### 2. Switch VLAN Configuration

[INSERT IMAGE: Vlan-Basics-12312149-ports.png]

**Description:**
This screenshot displays the output of `ovs-vsctl show`, confirming VLAN configuration. Ports eth1 and eth2 are assigned to VLAN 149, while ports eth3 and eth4 are assigned to VLAN 150.

---

### 3. IP Address Configuration

[INSERT IMAGE: host1_ipAddr.png]

**Description:**
This screenshot shows the IP configuration of Host1 using the `ip addr` command, confirming correct assignment of IP address.

---

### 4. Successful Ping (Same VLAN)

[INSERT IMAGE: ping_host1.png]

**Description:**
This screenshot shows successful communication between hosts in the same VLAN (Host1 to Host2), verifying intra-VLAN connectivity.

---

### 5. Failed Ping (Different VLAN)

[INSERT IMAGE: failedVlanPing.png]

**Description:**
This screenshot shows failed communication between different VLANs (Host1 to Host3), confirming VLAN isolation.

---

### 6. ARP Table

[INSERT IMAGE: vlan-arpn.png]

**Description:**
This screenshot shows the ARP table where hosts in the same VLAN have resolved MAC addresses, while hosts in different VLANs show incomplete entries.

---

## Result

VLAN segmentation was successfully implemented. Hosts in same VLAN communicated successfully, while hosts in different VLANs could not communicate.

---

# Task 2: Setup VLANs on Router

## Aim

To configure inter-VLAN routing using a Linux Router.

---

## Procedure

### Network Setup

* Linux Router added
* Router connected to switch eth0 (trunk port)

---

### IP Configuration

* VLAN 149 → 192.168.149.0/24
* VLAN 150 → 192.168.150.0/24

---

### Switch Configuration

* Access ports assigned VLANs
* eth0 configured as trunk port

---

### Router Configuration

* Subinterfaces created: eth0.149 and eth0.150
* IP forwarding enabled

---

### Testing

* Inter-VLAN communication → SUCCESS

---

## Screenshots (Task 2)

### 1. Network Topology

[INSERT IMAGE: ROUTER.png]

**Description:**
This screenshot shows the updated topology including the Linux router connected to the switch via port eth0.

---

### 2. Switch Configuration

[INSERT IMAGE: Vlan-Basics-12312149-ports.png]

**Description:**
This screenshot shows VLAN tagging and trunk configuration using `ovs-vsctl show`, confirming correct switch setup.

---

### 3. IP Forwarding

[INSERT IMAGE: ipForward.png]

**Description:**
This screenshot confirms that IP forwarding is enabled on the router, allowing packets to be routed between VLANs.

---

### 4. Inter-VLAN Ping

[INSERT IMAGE: HOSTpING_150.png]

**Description:**
This screenshot shows successful ping between hosts in different VLANs, confirming that inter-VLAN routing is working.

---

## Result

Inter-VLAN routing was successfully implemented. All hosts across VLANs communicated through the router.

---

# Conclusion

This lab demonstrated VLAN segmentation and inter-VLAN routing. VLANs isolated traffic, and the router enabled communication between VLANs.

---

**Note:** Insert all screenshots at the indicated positions before exporting to PDF.
