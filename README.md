# Enterprise Network Design using Cisco Packet Tracer with VLAN, DHCP, DNS and OSPF

## Overview

This project demonstrates the design and implementation of a small enterprise network using Cisco Packet Tracer.

The network includes multiple departments separated by VLANs, centralized DHCP and DNS services, Inter-VLAN Routing using Router-on-a-Stick, and dynamic routing between two sites using OSPF.

---

## Objectives

* Design a structured enterprise network
* Implement VLAN segmentation
* Configure Inter-VLAN Routing
* Deploy DHCP services
* Deploy DNS services
* Implement OSPF dynamic routing
* Verify end-to-end connectivity

---

## Network Topology

The network consists of:

### Headquarters

* HR Department (VLAN 10)
* Sales Department (VLAN 20)
* IT Department (VLAN 30)
* Server Network (VLAN 50)

### Branch Office

* Branch LAN (192.168.60.0/24)

### Routers

* Router1 (Headquarters)
* Router2 (Branch Office)

### Dynamic Routing

* OSPF Area 0

---

## VLAN Configuration

| VLAN | Department | Network         |
| ---- | ---------- | --------------- |
| 10   | HR         | 192.168.10.0/24 |
| 20   | Sales      | 192.168.20.0/24 |
| 30   | IT         | 192.168.30.0/24 |
| 50   | Servers    | 192.168.50.0/24 |

---

## Router-on-a-Stick

Router1 provides Inter-VLAN Routing using subinterfaces:

* G0/0.10
* G0/0.20
* G0/0.30
* G0/0.50

Each VLAN has its own default gateway.

---

## DHCP Configuration

A centralized DHCP server provides IP addresses to all VLANs.

### DHCP Pools

| VLAN  | Start Address  | Gateway      |
| ----- | -------------- | ------------ |
| HR    | 192.168.10.100 | 192.168.10.1 |
| Sales | 192.168.20.100 | 192.168.20.1 |
| IT    | 192.168.30.100 | 192.168.30.1 |

DHCP Relay was configured using:

ip helper-address 192.168.50.10

---

## DNS Configuration

DNS service is hosted on:

192.168.50.10

Configured records:

[www.company.local](http://www.company.local)
dns.company.local
files.company.local

---

## OSPF Configuration

OSPF Process ID: 1

Area: 0

### WAN Link

10.0.0.0/30

Router1: 10.0.0.1

Router2: 10.0.0.2

### Branch Network

192.168.60.0/24

Gateway: 192.168.60.1

---

## IP Addressing Plan

| Device          | IP Address    |
| --------------- | ------------- |
| Router1 G0/0.10 | 192.168.10.1  |
| Router1 G0/0.20 | 192.168.20.1  |
| Router1 G0/0.30 | 192.168.30.1  |
| Router1 G0/0.50 | 192.168.50.1  |
| Server          | 192.168.50.10 |
| Router1 G0/1    | 10.0.0.1      |
| Router2 G0/0    | 10.0.0.2      |
| Router2 G0/1    | 192.168.60.1  |
| Branch PC       | 192.168.60.10 |

---

## Verification Tests

### VLAN Connectivity

Successful ping from:

192.168.10.10

to

192.168.20.10

---

### DNS Resolution

Successful resolution of:

[www.company.local](http://www.company.local)

to

192.168.50.10

---

### OSPF Neighbor Adjacency

Verified using:

show ip ospf neighbor

State:

FULL

---

### End-to-End Connectivity

Successful ping:

192.168.10.10 → 192.168.60.10

Result:

0% packet loss

---

## Technologies Used

* Cisco Packet Tracer
* VLAN
* Trunking
* Router-on-a-Stick
* DHCP
* DNS
* OSPF

---

## Author

Amin Badparvar

Computer Engineering Student
