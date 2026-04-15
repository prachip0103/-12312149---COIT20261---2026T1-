# Week 1 Portfolio
## Objectives
The objective of this week’s tutorial was to become familiar with the basic functions of GNS3, including project creation, Linux host setup, static IP address configuration, annotations, and the use of Linux commands in the web console.

## Tasks Completed
In Week 1, I created a new GNS3 project named `GNS3-Intro-12312149`. I added one Linux Host node to the workspace and inserted text annotations showing the project title, my name, student ID, date, and unit details. I selected the IP address `10.10.1.1/24` for the host and labelled it near the node.

Before starting the node, I configured a static IP address through the `/etc/network/interfaces` file. After starting the host, I opened the web console and used the appropriate Linux command to verify that the IP address had been successfully assigned to the `eth0` interface.

 ## Configuration Used
```bash
auto eth0
iface eth0 inet static
   address 10.10.1.1
   netmask 255.255.255.0
   up sysctl net.ipv4.ip_forward=0
```
## IP Address
![ipaddress](./images/GNS3-Intro-12312149-ipaddress.png)
