# Experiment 8 — Logical Addressing (IPv4/IPv6) and ARP, RARP, BOOTP, DHCP

**Course:** Computer Networks Lab (ENCS304)  
**Institution:** KR Mangalam University  

---

## 🎯 Aim

Create a simulation to demonstrate logical addressing using IPv4 and IPv6. Implement address mapping techniques — ARP, RARP, BOOTP, and DHCP — to show how devices acquire and resolve network addresses.

---

## 📌 Objective

- Understand IPv4 and IPv6 addressing schemes and their differences.
- Simulate ARP (Address Resolution Protocol) for MAC-to-IP mapping.
- Configure a DHCP server to automatically assign IP addresses.
- Compare static and dynamic address assignment methods.

---

## 📖 Theory

### IPv4 vs IPv6
| Feature | IPv4 | IPv6 |
|---------|------|------|
| Address Length | 32-bit | 128-bit |
| Notation | Dotted decimal | Hexadecimal (colon-separated) |
| Total Addresses | ~4.3 billion | ~3.4 × 10³⁸ |
| Header Size | 20 bytes | 40 bytes |
| Example | 192.168.1.1 | 2001:0db8::1 |

### Address Resolution Protocols
| Protocol | Full Form | Purpose |
|----------|-----------|---------|
| ARP | Address Resolution Protocol | Resolve IP → MAC |
| RARP | Reverse ARP | Resolve MAC → IP (legacy) |
| BOOTP | Bootstrap Protocol | Static IP for diskless workstations |
| DHCP | Dynamic Host Configuration Protocol | Dynamic IP assignment |

---

## 🖧 Network Topology

> 📷 Add screenshots below:

- `screenshots/ipv4_network.png`
- `screenshots/ipv6_network.png`
- `screenshots/dhcp_server_config.png`
- `screenshots/arp_table.png`

---

## 🔧 Step-by-Step Procedure

### IPv4 Static Assignment
1. Create a network with 1 router, 1 switch, and 3 PCs.
2. Assign static IPs: `192.168.1.10/24`, `192.168.1.11/24`, `192.168.1.12/24`.
3. Use `arp -a` on each PC to view ARP table after ping.

### DHCP Configuration
1. Add a Server to the network.
2. Enable DHCP service on the server.
3. Set DHCP pool: Start IP `192.168.1.100`, Subnet `255.255.255.0`, Gateway `192.168.1.1`.
4. Set PCs to obtain IP automatically (DHCP).
5. Verify assigned IPs with `ipconfig`.

### IPv6 Configuration
1. Enable IPv6 on router interface.
2. Assign IPv6 addresses to PCs manually.
3. Test with `ping6`.

---

## ⚙️ Configuration Commands

```
! ---- DHCP Server Configuration on Router ----
Router(config)# ip dhcp pool LAN_POOL
Router(dhcp-config)# network 192.168.1.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.1.1
Router(dhcp-config)# dns-server 8.8.8.8
Router(dhcp-config)# lease 7

Router(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.10

! ---- ARP Verification ----
Router# show arp
PC> arp -a

! ---- IPv6 Configuration ----
Router(config)# interface GigabitEthernet0/0
Router(config-if)# ipv6 address 2001:db8:1::1/64
Router(config-if)# ipv6 enable
Router(config-if)# no shutdown

Router(config)# ipv6 unicast-routing
```

---

## 📊 Observations / Results

> 📷 Add output screenshots in the `screenshots/` folder.

| Device | Assigned IP | MAC Address | Method |
|--------|------------|-------------|--------|
| PC1 | 192.168.1.100 | — | DHCP |
| PC2 | 192.168.1.101 | — | DHCP |
| PC3 | 192.168.1.11  | — | Static |

---

## ✅ Conclusion

This experiment demonstrated how logical addressing works in IPv4 and IPv6 networks. DHCP simplifies network management by automating IP address assignment, while ARP ensures correct delivery at the data link layer.
