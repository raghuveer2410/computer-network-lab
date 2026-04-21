# Experiment 2 — Packet Switching vs Circuit Switching

**Course:** Computer Networks Lab (ENCS304)  
**Institution:** KR Mangalam University  

---

## 🎯 Aim

Create a network simulation to demonstrate packet switching and circuit switching. Compare the performance and efficiency of both methods by simulating a series of data transmission scenarios.

---

## 📌 Objective

- Understand the fundamental differences between packet switching and circuit switching.
- Simulate both switching methods and observe data flow.
- Compare performance metrics: latency, bandwidth utilization, and efficiency.

---

## 📖 Theory

**Circuit Switching** establishes a dedicated communication path between sender and receiver before data transfer begins. The path remains reserved for the entire session (e.g., traditional telephone networks).

**Packet Switching** divides data into small packets that are routed independently through the network. Each packet may take a different path and is reassembled at the destination (e.g., the Internet).

| Feature | Circuit Switching | Packet Switching |
|---------|-------------------|-----------------|
| Path | Fixed, dedicated | Dynamic, shared |
| Bandwidth | Reserved | On-demand |
| Delay | Low (once connected) | Variable |
| Efficiency | Low (idle waste) | High |
| Example | PSTN, ISDN | Internet, VoIP |

---

## 🖧 Network Topology

> 📷 Add screenshots below:

- `screenshots/circuit_switching_topology.png`
- `screenshots/packet_switching_topology.png`
- `screenshots/comparison_results.png`

---

## 🔧 Step-by-Step Procedure

1. Open Cisco Packet Tracer and design a multi-router network (e.g., 3 routers connecting 2 PCs).
2. **Circuit Switching Simulation:**
   - Configure a dedicated point-to-point serial link between source and destination.
   - Send data and observe that the path remains exclusively reserved.
3. **Packet Switching Simulation:**
   - Configure multiple routers with routing tables.
   - Send packets and observe different paths taken.
4. Use simulation mode in Packet Tracer to visualize packet movement.
5. Record observations: transmission time, path taken, and resource utilization.

---

## ⚙️ Configuration Commands

```
! Router basic configuration
Router> enable
Router# configure terminal
Router(config)# interface Serial0/0/0
Router(config-if)# ip address 10.0.0.1 255.255.255.252
Router(config-if)# no shutdown

! Static routing example
Router(config)# ip route 192.168.2.0 255.255.255.0 10.0.0.2

! Verify routing table
Router# show ip route
```

---

## 📊 Observations / Results

> 📷 Add output screenshots in the `screenshots/` folder.

| Parameter | Circuit Switching | Packet Switching |
|-----------|-------------------|-----------------|
| Setup Time | High | None |
| Transmission Delay | Low | Variable |
| Bandwidth Waste | Yes (idle reservation) | No |
| Fault Tolerance | Low | High |
| Suitable For | Voice calls | Data/Internet |

---

## ✅ Conclusion

This experiment demonstrated that packet switching is more efficient for data networks due to dynamic resource allocation and fault tolerance, while circuit switching is better suited for real-time voice communication where consistent latency is required.
