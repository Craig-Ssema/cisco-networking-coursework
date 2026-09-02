# Cisco Networking Coursework

Packet Tracer labs and network design projects from my networking courses at North American University, Spring 2025 through Spring 2026.

## spring-2025

Switching and routing labs: EtherChannel, router-on-a-stick inter-VLAN routing, extended IPv4 ACLs, and a site-to-site IPsec VPN configured from the CLI.

## fall-2025

The bulk of the coursework, 96 labs:

* Routing: static routes, RIPv2, EIGRP for IPv4 and IPv6, OSPF
* Switching: VLANs, VTP, STP, PVST, EtherChannel, port security
* Services: DHCPv4, static and dynamic NAT, PAT
* ACLs: numbered and named standard, extended, IPv6, and ACLs on VTY lines

`project/` holds the TechCorp enterprise network design: written documentation and interactive HTML topology diagrams.

## spring-2026

COMP 4358, Cloud Computing.

Packet Tracer labs cover IPv6 addressing and subnetting, WPA2-Enterprise WLAN on a wireless LAN controller, connectivity troubleshooting with ping, traceroute and ICMP, and device hardening with SSH.

`cloud-computing-labs/` is the Azure side:

* NSG rules limiting SSH to a single source IP, with a jump host reaching a private VM
* Load Balancer with NAT Gateway
* Application Gateway with Traffic Manager
* Azure VM web server build
* Bluetooth packet capture and analysis using Wireshark with the Bluetooth Test Platform

`project/` is the final project: TechNova, a wireless network for a three-story office. Dual-core Layer 3 distribution with HSRP gateways and LACP EtherChannels, OSPF between the cores and the edge router, seven lightweight APs registered to a WLC over CAPWAP with WPA2-Enterprise against RADIUS, and a management plane locked to SSH with NTP, syslog, BPDU Guard and guest VLAN isolation.

## Opening the files

`.pka` and `.pkt` files open in Cisco Packet Tracer, free through Cisco Networking Academy.
