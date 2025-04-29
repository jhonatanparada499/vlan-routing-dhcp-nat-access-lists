# Cisco VLAN Routing with DHCP and NAT Overload

## Overview

In order to support inter-VLAN routing, DHCP-based IP address assignment, NAT overload (PAT) for internet access, and ACL-based traffic restrictions between VLANs, this project shows how to configure a Cisco router and managed switch.

Isolated IP subnets were set up for both VLANs 2 and 3. An optional ACL was used to prevent VLAN2 from accessing VLAN3, and DHCP pools were set up on the router to serve hosts dynamically. The final configuration preserved selective internal segmentation while enabling internet access for both VLANs.
## Physical Topology

![](photos/Physical_Network_Topology.jpg)

## Logical Topology

![](photos/Logical_Network_Topology.png)

## Configurations

### Switch
- VLAN 2 and VLAN 3 created
- Access ports assigned for each VLAN
- Trunk port configured towards router

[`switch/Switch configuration.txt`](switch/Switch%20configuration.txt)

### Router
- Subinterfaces with 802.1Q encapsulation for each VLAN
- DHCP pools assigned to VLAN2 and VLAN3
- NAT Overload (PAT) configured for external internet access
- ACL applied to block VLAN2 from reaching VLAN3 (optional)

- [`router/Router configuration.txt`](router/Router%20configuration.txt) — Basic setup  
- [`router/Router configuration with access-li.txt`](router/Router%20configuration%20with%20access-li.txt) — Setup with ACL blocking  
- [`router/Router DHCP binding.txt`](router/Router%20DHCP%20binding.txt) — DHCP bindings  
- [`router/Router NAT translations.txt`](router/Router%20NAT%20translations.txt) — NAT table snapshot

## Validation

### VLAN2 VM – DHCP Lease and Configuration
![VLAN2 VM](photos/VM_in_VLAN2_Configuration.jpg)

### VLAN3 VM – DHCP Lease and Configuration
![VLAN3 VM](photos/VM_In_VLAN3_Configuration.jpg)

### VLAN3 Host Trying to Ping VLAN2 after applying ACL 
![Ping Test](photos/VM_in_VLAN3_Pinging_VLAN2.jpg)

## Technologies Used

- Cisco Router and Managed Switch (CLI Configuration)
- VLAN Configuration and Trunking (802.1Q)
- Router-on-a-Stick Inter-VLAN Routing
- DHCP Pools on Router
- NAT Overload (PAT) for Internet Access
- ACL for Inter-VLAN Access Control

## Notes

- Configurations saved after successful validation
- DHCP leases and NAT sessions captured live
- Physical workstation setup captured for reference
