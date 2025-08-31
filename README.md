IPv6 Lab Topology – Packet Tracer
📌 Overview

This lab demonstrates IPv6 network configuration using two labs (LAB 1 and LAB 2) connected through routers. Each lab has a router, switch, and a laptop connected to test end-to-end communication.

🖥️ Devices Used

2 Routers (2911)

2 Switches (2960-24TT)

2 Laptops

🌐 IPv6 Addressing Scheme
LAB 1

Router0 Fa0/0 → Switch0
2001:DB8:1:10::1/64

Laptop0 (via Switch0)
2001:DB8:1:10:290:CFF:FEE3:7D87/64

Router0 Fa0/1 → Router1 (link between labs)
2001:DB8:100::1/64

LAB 2

Router1 Fa0/0 → Switch1
2001:DB8:2:20::1/64

Laptop1 (via Switch1)
2001:DB8:2:20:230:F2FF:FE2C:61E1/64

Router1 Fa0/1 → Router0 (link between labs)
2001:DB8:100::2/64

🔧 Configuration Steps

Assign IPv6 addresses to all router interfaces:

Router(config)# ipv6 unicast-routing
Router(config)# interface fa0/0
Router(config-if)# ipv6 address 2001:DB8:1:10::1/64
Router(config-if)# no shutdown


(Repeat for other interfaces with correct IPv6 addresses.)

Configure IPv6 addresses on laptops:

Open Desktop > IP Configuration > IPv6

Enter the IPv6 address and subnet mask (/64).

Ensure default gateways on laptops point to respective router interfaces:

Laptop0 Gateway: 2001:DB8:1:10::1

Laptop1 Gateway: 2001:DB8:2:20::1

Test connectivity using ping:

From Laptop0 → Laptop1

From Laptop1 → Laptop0

From each Laptop → Both Routers

✅ Verification

Check IPv6 interface status:

Router# show ipv6 interface brief


Test pings across labs:

Laptop> ping 2001:DB8:2:20:230:F2FF:FE2C:61E1
Laptop> ping 2001:DB8:1:10:290:CFF:FEE3:7D87
