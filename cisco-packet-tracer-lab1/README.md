Cisco Packet Tracer Lab 1 – Basic Device Initialization & Network Setup

This lab provides complete hands-on practice for beginners learning Cisco networking.
You will configure routers, switches, PCs, static routing, VLAN management, and verify end-to-end connectivity.

🌐 Network Topology
[PC1] ---- [Switch1] ---- [Router1] ---- [Router2] ---- [Switch2] ---- [PC2]


All connections use Copper Straight-Through cable.

Both routers and switches are configured entirely through CLI.

🔧 PHASE 1 — Configure Routers
Router 1
enable
config t
int g0/0/0
 no shut
int g0/0/1
 no shut
exit
exit

Router 2
enable
config t
int g0/0/1
 no shut
int g0/0/0
 no shut
exit
exit

🔧 PHASE 2 — Configure Switches
Switch 1
enable
config t
hostname Switch1
enable secret class123

line console 0
 password cisco123
 login
exit

line vty 0 15
 password cisco123
 login
exit

interface vlan 1
 ip address 192.168.1.10 255.255.255.0
 no shut
exit

ip default-gateway 192.168.1.1
exit

Switch 2

(Only IP changes)

interface vlan 1
 ip address 192.168.2.10 255.255.255.0
 no shut
exit

ip default-gateway 192.168.2.1
exit

💻 PHASE 3 — Configure PC IP Addresses
PC1

IP: 192.168.1.2

Mask: 255.255.255.0

Gateway: 192.168.1.1

PC2

IP: 192.168.2.3

Mask: 255.255.255.0

Gateway: 192.168.2.1

🛣️ Static Routing
Router 1
config t
ip route 192.168.2.0 255.255.255.0 192.168.10.2
exit

Router 2
config t
ip route 192.168.1.0 255.255.255.0 192.168.10.1
exit

🔍 Verification Commands
PC1
ping 192.168.1.10
ping 192.168.1.1
ping 192.168.10.2
ping 192.168.2.3

Router 1
ping 192.168.2.3
show ip route
show interfaces description

Switch 1
show mac address-table
show vlan brief
show interfaces vlan 1
show ip interface brief

🐞 Troubleshooting Example

Shutdown interface to break connectivity:

config t
interface g0/0/1
 shutdown


Bring it back:

no shut

✔️ Lab Completion Checklist

 Console access into all devices

 Switch basic configuration completed

 Router interfaces configured

 Static routing implemented

 PC IP addresses assigned

 End-to-end ping successful

 Troubleshooting practiced
