# Dynamic Routing Network with RIP v2

## Project Overview

This project implements a dynamic routing network using **RIP version 2** across **5 routers** in a ring topology. RIP v2 is a classless, distance-vector routing protocol that supports **Variable Length Subnet Masking (VLSM)** and authentication. The network demonstrates full end-to-end connectivity between all routers and their loopback interfaces using dynamic route learning.

The topology consists of five Cisco routers (R1 to R5) connected in a closed loop, with each router having a dedicated Loopback0 interface for testing reachability.

---

## 📸 Screenshots

![App Screenshot](https://raw.githubusercontent.com/sarowarhosen01/Design-and-Implementation-of-a-Multi-Building-Campus-Network-/refs/heads/main/Screenshots/topology-overview.jpg)

## Key Features

- **Dynamic Routing**: Full implementation of RIP v2 for automatic route discovery and convergence.
- **VLSM Support**: Efficient use of IP address space with /30 subnets for point-to-point links.
- **Redundancy**: Ring topology provides alternate paths in case of link failure.
- **Loopback Testing**: Each router advertises its Loopback0 network.
- **Classless Routing**: Proper subnet mask propagation using RIP v2.
- **Complete Connectivity**: All routers can reach every other router and loopback network.

---

## Network Topology


**Physical Connections**:
- R1 ↔ R2
- R2 ↔ R3
- R3 ↔ R4
- R4 ↔ R5
- R5 ↔ R1

---

## IP Addressing Scheme

| Router | Interface   | IP Address      | Subnet Mask       | CIDR  | Connected To |
|--------|-------------|-----------------|-------------------|-------|--------------|
| R1     | G0/0        | 10.1.12.1      | 255.255.255.252   | /30   | R2 G0/0     |
| R1     | G0/1        | 10.1.15.1      | 255.255.255.252   | /30   | R5 G0/0     |
| R1     | Loopback0   | 192.168.1.1    | 255.255.255.0     | /24   | N/A         |
| R2     | G0/0        | 10.1.12.2      | 255.255.255.252   | /30   | R1 G0/0     |
| R2     | G0/1        | 10.1.23.1      | 255.255.255.252   | /30   | R3 G0/0     |
| R2     | Loopback0   | 192.168.2.1    | 255.255.255.0     | /24   | N/A         |
| R3     | G0/0        | 10.1.23.2      | 255.255.255.252   | /30   | R2 G0/1     |
| R3     | G0/1        | 10.1.34.2      | 255.255.255.252   | /30   | R4 G0/0     |
| R3     | Loopback0   | 192.168.3.1    | 255.255.255.0     | /24   | N/A         |
| R4     | G0/0        | 10.1.34.1      | 255.255.255.252   | /30   | R3 G0/1     |
| R4     | G0/1        | 10.1.45.1      | 255.255.255.252   | /30   | R5 G0/1     |
| R4     | Loopback0   | 192.168.4.1    | 255.255.255.0     | /24   | N/A         |
| R5     | G0/0        | 10.1.15.2      | 255.255.255.252   | /30   | R1 G0/1     |
| R5     | G0/1        | 10.1.45.2      | 255.255.255.252   | /30   | R4 G0/1     |
| R5     | Loopback0   | 192.168.5.1    | 255.255.255.0     | /24   | N/A         |

---

## Technologies & Protocols Used

- **Routing Protocol**: RIP Version 2 (with `no auto-summary`)
- **Simulation Tool**: Cisco Packet Tracer
- **Layer 3**: IPv4, Static and Dynamic Routing
- **Interfaces**: GigabitEthernet (G0/0, G0/1), Loopback interfaces
- **Protocols**: RIP, ICMP (for testing), ARP

---

## Project Files

- `Complite Project ipv6.pkt` - Main Packet Tracer project file (Note: Despite the name, the project uses IPv4 with RIP v2)

---

## How to Use

1. **Open the Project**:
   - Download and open `Complite Project ipv6.pkt` in **Cisco Packet Tracer** (version 8.0+ recommended).

2. **Verify Configuration**:
   - Check router configurations using:
     ```bash
     show ip interface brief
     show ip route
     show running-config

     ```

The network forms a **ring (cycle) topology**:
