# Experiment 3 — Packet Delay, Loss & Routing Algorithms

**Course:** Computer Networks Lab (ENCS304)  
**Institution:** KR Mangalam University  

---

## 🎯 Aim

Develop a network simulator to analyze packet delay, loss, and end-to-end throughput. Implement various routing algorithms and measure their impact on network performance under different traffic conditions.

---

## 📌 Objective

- Understand sources of packet delay and loss in computer networks.
- Implement and compare routing algorithms: Static Routing, RIP, and OSPF.
- Measure end-to-end throughput and latency under different network conditions.

---

## 📖 Theory

### Types of Delay
| Type | Description |
|------|-------------|
| **Processing Delay** | Time to examine packet header and determine output link |
| **Queuing Delay** | Time waiting in router queue |
| **Transmission Delay** | Time to push packet bits onto the link (L/R) |
| **Propagation Delay** | Time for signal to travel from source to destination |

### Routing Algorithms
- **Static Routing:** Routes manually configured by admin. Simple but doesn't adapt to changes.
- **RIP (Routing Information Protocol):** Distance-vector protocol using hop count as metric. Max 15 hops.
- **OSPF (Open Shortest Path First):** Link-state protocol using Dijkstra's algorithm. Scalable and fast convergence.

---

## 🖧 Network Topology

> 📷 Add screenshots below:

- `screenshots/network_topology.png`
- `screenshots/rip_routing_table.png`
- `screenshots/ospf_routing_table.png`
- `screenshots/ping_results.png`

---

## 🔧 Step-by-Step Procedure

1. Create a network with at least 4 routers and 4 PCs in Cisco Packet Tracer.
2. **Static Routing:**
   - Manually add routes using `ip route` commands.
   - Test connectivity with `ping` and `tracert`.
3. **RIP Configuration:**
   - Enable RIP on all routers.
   - Verify routes with `show ip rip database`.
4. **OSPF Configuration:**
   - Assign OSPF process and areas.
   - Verify with `show ip ospf neighbor` and `show ip route`.
5. Simulate high traffic and observe packet loss using extended ping.

---

## ⚙️ Configuration Commands

```
! ---- Static Routing ----
Router(config)# ip route 192.168.3.0 255.255.255.0 10.0.0.2

! ---- RIP Configuration ----
Router(config)# router rip
Router(config-router)# version 2
Router(config-router)# network 192.168.1.0
Router(config-router)# no auto-summary

! ---- OSPF Configuration ----
Router(config)# router ospf 1
Router(config-router)# network 192.168.1.0 0.0.0.255 area 0
Router(config-router)# network 10.0.0.0 0.0.0.3 area 0

! ---- Verification ----
Router# show ip route
Router# show ip ospf neighbor
Router# traceroute 192.168.3.1
```

---

## 📊 Observations / Results

> 📷 Add output screenshots in the `screenshots/` folder.

| Algorithm | Convergence Time | Metric Used | Max Hops | Scalability |
|-----------|-----------------|-------------|----------|-------------|
| Static    | N/A (manual)    | Manual      | Unlimited | Low |
| RIP v2    | Slow            | Hop Count   | 15       | Medium |
| OSPF      | Fast            | Cost (BW)   | Unlimited | High |

---

## ✅ Conclusion

This experiment demonstrated how routing algorithms affect network performance. OSPF showed faster convergence and better scalability compared to RIP, while static routing is suitable only for small, unchanging networks.
