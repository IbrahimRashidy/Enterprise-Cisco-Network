# 🚀 Enterprise Network Infrastructure — Cisco Packet Tracer

## 📌 Project Overview

A complete enterprise network infrastructure designed and implemented using **Cisco Packet Tracer**, covering enterprise switching, routing, redundancy, DHCP, NAT, security, and network management.

The project simulates a company network with multiple VLANs, redundant multilayer switches, dynamic routing, Internet connectivity, and centralized network services.

## 🏗️ Network Architecture

```text
                         ┌─────────────┐
                         │   Internet  │
                         │     ISP     │
                         │     R3      │
                         └──────┬──────┘
                                │
                         ┌──────┴──────┐
                         │     R0      │
                         │ Edge Router │
                         │ NAT / PAT  │
                         └──────┬──────┘
                           ┌────┴────┐
                           │         │
                         R1          R2
                           │         │
                    ┌──────┴─────────┴──────┐
                    │                       │
                 MLS0 ================== MLS1
                    │      EtherChannel      │
                    │                       │
                 Access Switches / End Devices
```

## 🔧 Technologies & Concepts Implemented

### Switching

* VLAN Configuration
* 802.1Q Trunking
* Inter-VLAN Routing
* Multilayer Switching
* SVI
* Spanning Tree Protocol (STP)
* Root Bridge / Secondary Root
* PortFast
* BPDU Guard
* EtherChannel
* LACP

### Routing

* Static Routing
* Default Routing
* OSPF
* OSPF Area 0
* Route Summarization
* Default Route Advertisement

### High Availability

* HSRP
* Active / Standby Gateway Redundancy
* STP Redundancy
* EtherChannel Link Redundancy

### Network Services

* DHCP
* DHCP Relay
* NTP
* SNMP

### NAT

* Dynamic PAT
* Static NAT
* Inside Local / Inside Global
* NAT Overload

### Security

* Extended ACL
* Traffic Filtering
* Port Security concepts
* SSH Management
* Network Device Hardening

## 🌐 VLAN Design

| VLAN | Department | Network       |
| ---- | ---------- | ------------- |
| 10   | HR         | 10.10.10.0/24 |
| 20   | IT         | 10.10.20.0/24 |
| 30   | Sales      | 10.10.30.0/24 |
| 40   | Finance    | 10.10.40.0/24 |
| 50   | Servers    | 10.10.50.0/24 |
| 99   | Management | 10.10.99.0/24 |

## 🔄 Routing Design

The internal network uses **OSPF Area 0** to exchange routes between the multilayer switches and routers.

The edge router provides the default route toward the ISP.

A summarized route is configured on the ISP router:

```text
10.10.0.0/16
```

This represents the internal enterprise networks and provides a simplified return path.

## 🔐 NAT & PAT

PAT allows multiple internal hosts to share the public IP address of the edge router.

```text
Inside Local
10.10.x.x
      ↓
     R0
      ↓
Inside Global
203.0.113.1
```

A Static NAT mapping was also configured for the internal Web Server:

```text
10.10.50.20
      ↓
203.0.113.3
```

## 🛡️ ACL Implementation

An Extended ACL was implemented to restrict access from the Sales VLAN to the internal Web Server while maintaining normal Internet access.

```text
Sales VLAN → Web Server    ❌
Sales VLAN → Internet      ✅
```

## 🔁 High Availability

HSRP was implemented between MLS0 and MLS1 to provide a redundant default gateway.

```text
Virtual Gateway
10.10.x.1

MLS0 → Active
MLS1 → Standby
```

If the Active multilayer switch fails, the Standby switch can take over the gateway role.

## 📡 Network Management

NTP was configured to synchronize the network devices with a centralized time source.

SNMP community configuration was also implemented on network devices for monitoring integration with an external NMS.

## 🧪 Testing & Verification

The network was tested using:

```text
ping
traceroute
show ip route
show ip ospf neighbor
show standby brief
show spanning-tree
show etherchannel summary
show ip nat translations
show access-lists
show ntp status
show ip ssh
```

Testing confirmed connectivity, routing, redundancy, NAT/PAT operation, ACL filtering, and network management functionality.

## 🎯 Project Objectives

* Build an enterprise-style Cisco network from scratch.
* Practice CCNA-level routing and switching concepts.
* Implement network redundancy and fault tolerance.
* Configure secure network access.
* Simulate Internet connectivity.
* Troubleshoot real-world networking problems.
* Develop practical experience with Cisco IOS and Packet Tracer.

## 🧠 Skills Demonstrated

**Cisco IOS • CCNA • Routing • Switching • OSPF • VLAN • STP • HSRP • EtherChannel • LACP • DHCP • NAT • PAT • ACL • NTP • SNMP • Network Security • Troubleshooting • Cisco Packet Tracer**

## 📁 Project Files

```text
📦 Enterprise-Cisco-Network
 ├── 📄 README.md
 ├── 📁 Packet-Tracer
 │   └── Enterprise-Network.pkt
 ├── 📁 Documentation
 │   └── Network-Topology.png
```

## 👨‍💻 Author

**Ibrahim Rashidy**

**Junior IT / Network Engineer**

Focused on **Cisco Networking, CCNA, Network Administration, and IT Infrastructure**.