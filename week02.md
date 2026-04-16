## Task 1: Setting Static IP Addresses
## Aim
The aim of this task was to configure static IP addresses on Linux hosts using three different methods in GNS3. These methods included using the GNS3 Configure menu, editing the /etc/network/interfaces file, and using the ip address add command.

## Topology Setup
A project named Setting-IP-12312149 was created in GNS3. The topology consisted of four Linux hosts and one Ethernet switch connected in the same LAN. The IPv4 network 10.10.1.0/24 was used.
The IP addresses assigned were:
Host1: 10.10.1.1/24
Host2: 10.10.1.2/24
Host3: 10.10.1.3/24
Host4: 10.10.1.4/24

-> GNS3 topology showing four Linux hosts connected to one Ethernet switch.
![Network](./images/week02/Setting-IP-12312149-network.png)
This screenshot shows the complete network topology created in GNS3. It contains four Linux hosts connected to a single Ethernet switch in the same LAN.

Host1 and Host2 Configuration
Host1 and Host2 were configured using the GNS3 Configure menu before starting the nodes. This method applies the IP settings automatically when the hosts are started.

1) Host1 IP address verification.
![Host1](./images/week02/Setting-IP-12312149-host1.png)
This screenshot shows the console output of Host1 using the Ip address show command. It confirms that Host1 was assigned the IP address 10.10.1.1/24.

 	
2) Host2 IP address verification.
![Host2](./images/week02/ Setting-IP-12312149-host2.png)
This screenshot shows the console output of Host2 using the Ip address show command. It confirms that Host2 was assigned the IP address 10.10.1.2/24.
