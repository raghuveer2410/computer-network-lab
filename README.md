# CN-Lab — Computer Networks Lab (ENCS304)

**KR Mangalam University — School of Engineering and Technology**  
**B.Tech CSE / AI-ML / Data Science / Cyber / UX-UI / FSD | 2025–2026**

---

## 📋 Course Outcomes

| CO | Description |
|----|-------------|
| CO1 | Understand fundamental concepts: network devices, IP addressing, VLANs, and routing protocols |
| CO2 | Develop practical skills in setting up/configuring wired and wireless networks |
| CO3 | Configure advanced features: VLANs, inter-VLAN routing, static routing, and NAT |
| CO4 | Design and implement error detection/correction using Hamming Codes and CRC |

---

## 📁 Repository Structure

```
CN-Lab/
│
├── Experiment-1/    → Network Topologies (Bus, Star, Ring, Mesh)
├── Experiment-2/    → Packet Switching vs Circuit Switching
├── Experiment-3/    → Packet Delay, Loss & Routing Algorithms
├── Experiment-4/    → Error Detection & Correction (Block Coding & CRC)
├── Experiment-5/    → Flow Control & ARQ Protocols
├── Experiment-6/    → Multiple Access Protocols (ALOHA, CSMA/CD, CSMA/CA)
├── Experiment-7/    → Sliding Window Protocol with Piggybacking
├── Experiment-8/    → Logical Addressing (IPv4/IPv6) & ARP/DHCP
├── Experiment-9/    → Transport Layer Protocols (UDP, TCP, SCTP)
├── Experiment-10/   → DNS and DDNS Simulation
└── Experiment-11/   → HTTP & WWW Web Server Simulation
```

# Computer-Network
Lab Assignments


**Experiment - 1**

Design and simulate a simple computer network using various connection topologies (bus, star, ring, mesh). Compare the advantages and disadvantages of each topology in terms of data flow and network efficiency.

BUS TOPOLOGY 

Steps:
1. Open Cisco Packet Tracer
2. Drag 4–5 PCs
3. Drag 1 Hub
4. Connect all PCs to the hub using Copper Straight-through cables
5. Assign IP addresses:
PC1 → 192.168.1.1
PC2 → 192.168.1.2
PC3 → 192.168.1.3
6. Use Add Simple PDU (envelope icon) to send packets
7. Observe packet flow (shared medium behavior)

STAR TOPOLOGY

Steps:
1. Place 1 Switch
2. Add 4–6 PCs
3. Connect each PC to the switch using Straight-through cable
4. Assign IPs (same network):
192.168.2.x
5. Send PDU between PCs
6. Observe: communication via central switch

RING TOPOLOGY

Steps:
1. Packet Tracer does not directly support ring via a single device, so simulate manually:
2. Place 4 PCs
Connect:
PC1 → PC2
PC2 → PC3
PC3 → PC4
PC4 → PC1
3. Use Cross-over cables
4. Assign IPs (same network: 192.168.3.x)
5. Send PDU and observe circular path

MESH TOPOLOGY

Steps:
1. Place 4 PCs
2. Connect each PC to every other PC
3. Use Cross-over cables
4. Assign IPs:
192.168.4.x
5. Send PDU
6. Observe multiple paths for data

HYBRID TOPOLOGY

Steps:
1. Add 2 Switches + 1 Hub + PCs
2. PCs → Switches (Star)
3. Switches → Hub (Bus backbone)
4. Test → observe combined behavior

**Experiment - 2**

Create a network simulation to demonstrate packet switching and circuit switching. Compare the performance and efficiency of both methods by simulating a series of data transmission scenarios.

What is Circuit Switching?

Circuit switching is a method where a dedicated path is established between sender and receiver before data transmission.

Steps:-

1. Create a network with two PCs connected through routers via a single path.
2. Connect devices using appropriate cables.
3. Assign IP addresses to PCs and router interfaces.
4. Enable router interfaces using no shutdown.
5. Configure static routing to establish a fixed path.
6. Send data using ping from source to destination.
7. Observe that all packets follow the same path.
8. Note that the path remains reserved during communication.
9. Verify successful data transmission.
10. Conclude that communication uses a dedicated path.

What is Packet Switching?

Packet switching is a method where data is divided into small packets and sent through different paths in a network to reach the destination.

Steps:-

1. Create a network with multiple PCs connected through a switch.
2. Connect all PCs to the switch using straight-through cables.
3. Assign IP addresses to all PCs in the same network.
4. Switch to Simulation Mode.
5. Send a PDU from one PC to another.
6. Observe packets being divided and transmitted across the network.
7. Track packet movement through the switch.
8. Verify successful packet delivery at destination.
9. Repeat for different PCs to observe communication.
10. Conclude that data is transmitted in the form of packets.

**Experiment - 3**

Develop a network simulator to analyze packet delay, loss, and end-to-end throughput. Implement various routing algorithms and measure their impact on network performance under different traffic conditions.

Steps:- 

1. Create a network with two PCs connected via a switch.
2. Assign IP addresses in the same network.
3. Ping between PCs to verify connectivity.
4. Start continuous ping.
5. Disconnect cable to simulate link failure.
6. Observe packet loss and timeout.
7. Reconnect cable to restore link.
8. Observe recovery of communication.
9. Record failure and recovery behavior.
10. Conclude impact of link errors.

**Experiment - 6**

Develop a simulation to demonstrate multiple access protocols such as Pure ALOHA, Slotted ALOHA, CSMA/CD, and CSMA/CA. Analyze the performance of each protocol in handling network collisions and maximizing data transmission efficiency.

CSMA/CA is a network protocol used in wireless networks (Wi-Fi) to avoid collisions before they happen.

Steps:-

1. Sense channel
2. If idle → Wait (IFS time)
3. Send RTS (Request to Send)
4. Receive CTS (Clear to Send)
5. Transmit data
6. Receive ACK
7. If no ACK → Retransmit

CSMA/CD is a network protocol used in wired Ethernet LANs to control how devices share a communication channel.

Steps:-
1. Sense the channel – Device checks if medium is idle
2. If idle → Transmit data
3. If busy → Wait
4. During transmission → Detect collision
5. If collision occurs → Send jam signal
6. Stop transmission
7. Wait (Backoff time)
8. Retransmit



**Experiment - 7**

Create a simulation to demonstrate logical addressing using IPv4 and IPv6. Implement address mapping techniques such as ARP and DHCP to show how devices acquire and resolve network addresses.

**ARP**

ARP is used to map an IP address to its corresponding MAC address in a local network.

STEPS:-

1. Create a network with one switch and multiple PCs.
2. Connect PCs using straight-through cables.
3. Assign IP addresses in the same subnet (e.g., 192.168.1.x).
4. Switch to Simulation Mode.
5. Send a PDU from source PC to destination PC.
6. Observe ARP request broadcast in the network.
7. Observe ARP reply from destination PC with MAC address.
8. Open packet details to verify IP–MAC mapping.
9. Continue simulation to complete ICMP communication.
10. Verify ARP resolution in the process.

**DHCP**

DHCP is used to automatically assign IP address, subnet mask, gateway, and DNS to devices in a network.

STEPS:-

1.Create a network with one server, one switch, and multiple PCs.
2. Connect server and PCs to the switch using straight-through cables.
3. Assign a static IP to the server (e.g., 10.0.0.1).
4. Open server → Services → DHCP and turn DHCP service ON.
5. Create a DHCP pool and set network (10.0.0.0) with subnet mask.
6. Configure default gateway (e.g., 10.0.0.1) and DNS server.
7. Set starting IP range (e.g., 10.0.0.2 onwards).
8. Save the DHCP configuration.
9. Set all PCs to DHCP mode in IP configuration.
10. Verify PCs receive IP addresses automatically and test using ping.

**Experiment - 9**

Implement a transport layer simulation to demonstrate process-to-process   communication using UDP, TCP, and SCTP. Compare the protocols in terms of connection establishment, data transmission, and congestion control.

Steps:-

Here are **one-line steps for RIP practical**:

1. Assign IP addresses to all router interfaces.
2. Configure IP and default gateway on all PCs.
3. Enable router interfaces using `no shutdown`.
4. Start RIP using `router rip` command.
5. Set RIP version using `version 2`.
6. Disable auto summarization using `no auto-summary`.
7. Add all connected networks using `network` command.
8. Repeat RIP configuration on all routers.
9. Verify routing table using `show ip route`.
10. Test connectivity using `ping` between PCs.


**Experiment - 10**

Implement a DNS and DDNS simulation to demonstrate domain name resolution and dynamic updates. Create a simple client-server application that queries and updates the DNS records.

What is DNS?

DNS is a system that converts domain names into IP addresses for communication over the internet.

Steps:-

1. Create a DNS server using sockets to store domain–IP mappings.
2. Start the server and listen for incoming client connections.
3. Design a client program to send requests to the server.
4. Send a QUERY request to resolve a domain name to an IP address.
5. Server processes the request and returns the corresponding IP.
6. Send an UPDATE request to add or modify DNS records dynamically.
7. Server updates the record in its database/dictionary.
8. Display the server response on the client side.
9. Repeat requests to demonstrate real-time DNS resolution and updates.

Practical Steps:-

1. Assign IP address to PC0 → 192.168.1.10
2. Assign IP to DNS Server → 192.168.1.100
3. Assign IP to Web Server → 192.168.1.200
4. On PC0, set DNS Server IP = 192.168.1.100
5. Open DNS Server → Services → DNS → Turn ON
6. Add DNS record:
Name: www.krmu.edu
Address: 192.168.1.200
7. On Web Server → Services → HTTP → Turn ON
8. Go to PC0 → Desktop → Web Browser
Enter URL: www.krmu.edu
9. DNS resolves domain → connects to Web Server → webpage loads

Each experiment folder contains:
- `README.md` — Full lab report
- `experiment.pkt` — Cisco Packet Tracer / simulation file *(add your file)*
- `config.txt` — Router/switch configuration commands *(if applicable)*
- `screenshots/` — Topology and output screenshots *(add your screenshots)*

---

## 📅 Assignment Schedule

| # | Experiment | Released After | Duration |
|---|-----------|----------------|----------|
| 1 | Network Topologies | Session 4 | 1 week |
| 2 | Packet Switching vs Circuit Switching | Session 10 | 2 weeks |
| 3 | Packet Delay, Loss & Routing Algorithms | Session 15 | 1 week |
| 4 | Error Detection & Correction | Session 20 | 1 week |
| 5 | Flow Control & ARQ Protocols | Session 24 | 2 weeks |
| 6 | Multiple Access Protocols | Session 26 | 1 week |
| 7 | Sliding Window Protocol | Session 27 | 1 week |
| 8 | Logical Addressing & ARP/DHCP | Session 30 | 2 weeks |
| 9 | Transport Layer Protocols | Session 35 | 1 week |
| 10 | DNS and DDNS Simulation | Session 40 | 2 weeks |
| 11 | HTTP & WWW Simulation | Session 41 | 1 week |

---

## 🛠️ Tools Used

- **Cisco Packet Tracer** — Network topology design and simulation
- **Python** — Protocol simulation scripts
- **GitHub** — Version control and lab submission

---

## 👤 Student Details

| Field | Value |
|-------|-------|
| Name | *(Raghuveer Diya)* |
| Roll No. | *(2301010268)* |
| Section | *(D)* |
| Branch | *(CSE)* |
| Faculty | *(Rajesh)* |
