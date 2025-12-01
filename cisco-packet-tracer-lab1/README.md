Cisco Packet Tracer Lab 1 – Basic Device Initialization & Network Setup

This lab provides complete hands-on practice for beginners learning Cisco networking.
You will configure routers, switches, PCs, static routing, VLAN management, and verify end-to-end connectivity.

🌐 Network Topology
[PC1] ---- [Switch1] ---- [Router1] ---- [Router2] ---- [Switch2] ---- [PC2]

- All are connected using **Copper Straight-Through** cable.
- Few ports were down so do basic configuration using CLI mode of both routers using these basic commands and check router interface, if it is up or not;

  
## **PHASE : 1 - Configure Routers**

- Router1

  ***>enable***

  ***>config t***

  ***>int gigabitethernet0/0/0***

  ***>no shut***

  ***>Interface GigabitEthernet0/0/1***

  ***>no shut***

  ***>exit
 >exit***

- Router 2

***>enable***

  ***>config t***

  ***>int gigabitethernet0/0/1***

  ***>no shut***

  ***>Interface GigabitEthernet0/0/0***

  ***>no shut***

  ***>exit
 >exit***

## **PHASE : 2 - Configure Switches**

- Now lets do Initial device configuration:
- Switch 1 & Switch 2

***>enable
>config t
>hostname Switch1 (to set hostname)
>enable secret class123 (to set privileged exec password)
>line console 0 (to set console password)
>password cisco123
>login
>exit
>line vty 0 15 (set vty for remote access)
>password cisco123
>login
>exit***

  ***>interface vlan 1 (to configure management interface)
    >ip address 192.168.1.10 255.255.255.0
    >no shut
 >exit
 >ip default-gateway 192.168.1.1 (set default gateway)
>exit***

- Switch 2( just change IP other remain same as S1)

***>interface vlan 1
    >ip address 192.168.2.10 255.255.255.0
    >no shut
 >exit
 >ip default-gateway 192.168.2.1
>exit***

---

## **PHASE : 3 - Configure IP Addresses**

- PC 1

**IP Address:** 192.168.1.2

**Subnet Mask:** 255.255.255.0

**Default Gateway:** 192.168.1.1

- PC 2

**IP Address:** 192.168.1.3

**Subnet Mask:** 255.255.255.0

**Default Gateway:** 192.168.2.1

Now all devices are configured sucessfully and what i see;

- **Switch1 prompt:** `Switch1#`
- **Switch2 prompt:** `Switch2#`
- **Router1 prompt:** `Router1#`
- **Router2 prompt:** `Router2#`

Now to Verify Switch Configuration:

```
***Switch1# show interfaces vlan 1
Switch1# show ip interface brief***
```

- To configure Static Routing on routers:

***Router1# configure terminal
Router1(config)# ip route 192.168.2.0 255.255.255.0 192.168.10.2
Router1(config)# exit***

***Router2# configure terminal
Router2(config)# ip route 192.168.1.0 255.255.255.0 192.168.10.1
Router2(config)# exit***

- For Basic Connectivity Test i do;

# From PC1 command prompt

PC1> ping 192.168.1.10    (Switch1)
PC1> ping 192.168.1.1      (Router1)
PC1> ping 192.168.10.2    (Router2)
PC1> ping 192.168.2.100   (PC2)

# From Router1

Router1# ping 192.168.2.100
Router1# show ip route
Router1# show interfaces description

# From Switch1

Switch1# show mac address-table
Switch1# show vlan brief

- **Troubleshooting:**

I do shutdown interface and then test it for troubleshooting practice;

***Router1# config t
Router1(config)# interface gigabitethernet 0/0/1
Router1(config-if)# shutdown***

I do test connectivity between PC1 & PC2, so then i bring interface up by using no shut command.

This comprehensive lab gives me hands-on practice with all fundamental Cisco networking concepts

## **Lab Completion Checklist**

- Successfully console into all devices
- Configure basic settings on both switches
- Configure basic settings on both routers
- Establish physical connections correctly
- Configure PC IP addresses
- Set up static routing
- Verify end-to-end connectivity
- Practice troubleshooting scenarios
