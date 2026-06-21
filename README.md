# packet-tracer-labs
Networking practice labs
# 🖧 Static Routing Lab Project

## 📌 Project Overview
This lab demonstrates **static routing** across three Cisco ISR4331 routers in Packet Tracer.  
Each router connects to a unique LAN, and static routes are configured to enable communication between all networks.

---

## 🗂 Topology
- **Router0 → PC0**: `200.10.1.0/24`
- **Router1 → PC1**: `172.16.0.0/16`
- **Router2 → PC2**: `10.0.0.0/8`
- **Router0 ↔ Router1**: `192.168.1.0/24`
- **Router1 ↔ Router2**: `192.167.1.0/24`

---

## ⚙️ Configuration

### Router0
```bash
interface g0/0
 ip address 200.10.1.1 255.255.255.0
 no shutdown

interface s0/2/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
R1
interface g0/0
 ip address 172.16.0.1 255.255.0.0
 no shutdown

interface s0/2/0
 ip address 192.168.1.2 255.255.255.0
 no shutdown

interface s0/2/1
 ip address 192.167.1.1 255.255.255.0
 no shutdown

ip route 200.10.1.0 255.255.255.0 192.168.1.1
ip route 10.0.0.0 255.0.0.0 192.167.1.2

R2
interface g0/0
 ip address 10.0.0.1 255.0.0.0
 no shutdown

interface s0/2/0
 ip address 192.167.1.2 255.255.255.0
 no shutdown

ip route 200.10.1.0 255.255.255.0 192.167.1.1
ip route 172.16.0.0 255.255.0.0 192.167.1.1


Ping from PC0 → PC1 and PC0 → PC2
Ping from PC2 → PC0
Successful replies confirm static routes are working across all routers.

ip route 172.16.0.0 255.255.0.0 192.168.1.2
ip route 10.0.0.0 255.0.0.0 192.168.1.2
