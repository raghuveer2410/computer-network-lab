# Experiment 1 — Network Topologies (Bus, Star, Ring, Mesh)

**Course:** Computer Networks Lab (ENCS304)  
**Institution:** KR Mangalam University  

---

## 🎯 Aim

Design and simulate a simple computer network using various connection topologies — Bus, Star, Ring, and Mesh. Compare the advantages and disadvantages of each topology in terms of data flow and network efficiency.

---

## 📌 Objective

- Design four distinct network topologies in Cisco Packet Tracer.
- Simulate data transmission across each topology.
- Compare performance in terms of fault tolerance, cost, and efficiency.
- Analyze the impact of topology on real-time and multimedia applications.

---

## 📖 Theory

A **network topology** defines the physical or logical arrangement of devices in a network.

| Topology | Description |
|----------|-------------|
| **Bus** | All devices share a single communication line (backbone). Simple but prone to collisions. |
| **Star** | All devices connect to a central hub/switch. Easy to manage; central point of failure. |
| **Ring** | Devices form a closed loop. Data travels in one direction; failure of one node can break the ring. |
| **Mesh** | Every device connects to every other device. Highly fault-tolerant but expensive to implement. |

---

## 🖧 Network Topology

> 📷 Add screenshots below after simulation:

| Topology | Screenshot |
|----------|------------|
| Bus | `screenshots/bus_topology.png` |
| Star | `screenshots/star_topology.png` |
| Ring | `screenshots/ring_topology.png` |
| Mesh | `screenshots/mesh_topology.png` |

---

## 🔧 Step-by-Step Procedure

1. Open Cisco Packet Tracer and create a new workspace.
2. **Bus Topology:** Add PCs and connect them via a Hub using Copper Straight-Through cables in a linear fashion.
3. **Star Topology:** Place a central Switch; connect all PCs to it using Copper Straight-Through cables.
4. **Ring Topology:** Connect PCs in a circular arrangement; each PC connects to the next forming a ring.
5. **Mesh Topology:** Connect every PC to every other PC using direct links.
6. Assign IP addresses to all devices (e.g., `192.168.1.x/24`).
7. Use the `ping` command to test connectivity between all nodes in each topology.
8. Capture screenshots of each topology and ping results.

---

## ⚙️ Configuration Commands

```
! Assigning IP address on a PC (Desktop > IP Configuration)
IP Address:     192.168.1.x
Subnet Mask:    255.255.255.0
Default Gateway: 192.168.1.1

! Testing connectivity
ping 192.168.1.2
ping 192.168.1.3
```

---

## 📊 Observations / Results

> 📷 Add output screenshots in the `screenshots/` folder and reference them here.

| Topology | Ping Success | No. of Devices | Cables Required |
|----------|-------------|----------------|-----------------|
| Bus      | ✅ / ❌      | 4              | n−1             |
| Star     | ✅ / ❌      | 4              | n               |
| Ring     | ✅ / ❌      | 4              | n               |
| Mesh     | ✅ / ❌      | 4              | n(n−1)/2        |

---

## ✅ Conclusion

Through this experiment, we successfully designed and simulated four network topologies using Cisco Packet Tracer. Each topology demonstrated unique characteristics in terms of data flow, fault tolerance, and resource usage. The star topology proved most practical for modern LANs due to ease of management, while mesh topology offered the highest fault tolerance at a greater cost.
