# Experiment 6 — Multiple Access Protocols (ALOHA, CSMA/CD, CSMA/CA)

**Course:** Computer Networks Lab (ENCS304)  
**Institution:** KR Mangalam University  

---

## 🎯 Aim

Develop a simulation to demonstrate multiple access protocols — Pure ALOHA, Slotted ALOHA, CSMA/CD, and CSMA/CA. Analyze the performance of each protocol in handling network collisions and maximizing data transmission efficiency.

---

## 📌 Objective

- Understand how multiple devices share a single communication channel.
- Simulate collision scenarios and observe resolution mechanisms.
- Compare throughput and efficiency of each protocol.

---

## 📖 Theory

Multiple Access protocols control how multiple nodes share a broadcast channel.

| Protocol | When to Transmit | Collision Handling | Max Throughput |
|----------|-----------------|-------------------|----------------|
| Pure ALOHA | Anytime | Retransmit after random delay | 18.4% |
| Slotted ALOHA | At slot boundaries | Retransmit in random future slot | 36.8% |
| CSMA/CD | Sense channel first | Detect collision, backoff (Ethernet) | ~100% (low load) |
| CSMA/CA | Sense + wait + RTS/CTS | Avoid collision before transmitting (Wi-Fi) | ~100% (low load) |

### ALOHA Throughput
- **Pure ALOHA:** S = G × e^(−2G), max at G = 0.5 → S ≈ 0.184
- **Slotted ALOHA:** S = G × e^(−G), max at G = 1 → S ≈ 0.368

---

## 🖧 Network Topology

> 📷 Add screenshots below:

- `screenshots/csma_cd_topology.png`
- `screenshots/csma_ca_topology.png`
- `screenshots/collision_detected.png`
- `screenshots/throughput_comparison.png`

---

## 🔧 Step-by-Step Procedure

### CSMA/CD (Wired LAN — Cisco Packet Tracer)
1. Create a hub-based LAN with 4 PCs (hub doesn't filter collisions).
2. Connect all PCs to a Hub using Copper Straight-Through cables.
3. Send simultaneous pings from multiple PCs and observe collisions.
4. Upgrade to a Switch and compare — switches eliminate collisions.

### CSMA/CA (Wireless LAN)
1. Add a Wireless Router and connect 3 laptops via Wi-Fi.
2. Configure SSID and WPA2 password.
3. Send pings and observe RTS/CTS mechanism in simulation mode.

---

## ⚙️ Configuration Commands

```
! Wireless Router Configuration
Router(config)# interface Dot11Radio0
Router(config-if)# ssid CN_Lab_Network
Router(config-if-ssid)# authentication open
Router(config-if-ssid)# guest-mode
Router(config-if)# no shutdown

! Verify wireless clients
Router# show dot11 associations

! CSMA/CD - Switch vs Hub comparison
! Use HUB for collision demo, SWITCH for collision-free
```

```python
# Pure ALOHA Throughput Simulation
import math

def pure_aloha(G):
    return G * math.exp(-2 * G)

def slotted_aloha(G):
    return G * math.exp(-G)

for G in [0.1, 0.5, 1.0, 1.5, 2.0]:
    print(f"G={G}: Pure={pure_aloha(G):.3f}, Slotted={slotted_aloha(G):.3f}")
```

---

## 📊 Observations / Results

> 📷 Add output screenshots in the `screenshots/` folder.

| Protocol | Channel Load (G) | Throughput | Collisions | Use Case |
|----------|-----------------|-----------|-----------|---------|
| Pure ALOHA | 0.5 | 18.4% | High | Satellite |
| Slotted ALOHA | 1.0 | 36.8% | Medium | RFID |
| CSMA/CD | Low | High | Detected & resolved | Ethernet |
| CSMA/CA | Low | High | Avoided | Wi-Fi |

---

## ✅ Conclusion

CSMA/CD and CSMA/CA are significantly more efficient than ALOHA protocols for wired and wireless networks respectively. ALOHA's simplicity makes it suitable only for low-traffic environments such as satellite communications.
