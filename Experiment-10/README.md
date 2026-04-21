# Experiment 10 — DNS and DDNS Simulation

**Course:** Computer Networks Lab (ENCS304)  
**Institution:** KR Mangalam University  

---

## 🎯 Aim

Implement a DNS and DDNS simulation to demonstrate domain name resolution and dynamic updates. Create a simple client-server application that queries and updates the DNS records.

---

## 📌 Objective

- Understand how DNS resolves domain names to IP addresses.
- Simulate DNS query and response mechanisms.
- Implement DDNS (Dynamic DNS) to demonstrate automatic record updates.
- Configure a DNS server in Cisco Packet Tracer.

---

## 📖 Theory

### DNS (Domain Name System)
DNS is a hierarchical naming system that translates human-readable domain names (e.g., `www.google.com`) into IP addresses (e.g., `142.250.190.4`).

**DNS Resolution Process:**
1. Client queries local DNS cache.
2. If not found → query Recursive Resolver.
3. Resolver queries Root Server → TLD Server → Authoritative Server.
4. IP address returned to client.

### DNS Record Types
| Record | Purpose | Example |
|--------|---------|---------|
| A | Maps domain → IPv4 | `example.com → 93.184.216.34` |
| AAAA | Maps domain → IPv6 | `example.com → 2606::...` |
| CNAME | Alias record | `www → example.com` |
| MX | Mail server | `mail.example.com` |
| PTR | Reverse lookup | `IP → domain` |

### DDNS (Dynamic DNS)
DDNS automatically updates DNS records when a device's IP address changes, enabling access to devices with dynamic IPs via a consistent hostname.

---

## 🖧 Network Topology

> 📷 Add screenshots below:

- `screenshots/dns_server_config.png`
- `screenshots/dns_resolution_demo.png`
- `screenshots/nslookup_output.png`
- `screenshots/ddns_update.png`

---

## 🔧 Step-by-Step Procedure

### DNS Server in Cisco Packet Tracer
1. Add a Server to the network and enable DNS Service.
2. Add DNS records:
   - `www.cnlab.com → 192.168.1.100`
   - `mail.cnlab.com → 192.168.1.101`
3. Configure all PCs to use the DNS server IP.
4. Open browser on a PC and type `www.cnlab.com` — observe resolution.

### Python DNS Simulation
1. Create a simple DNS server using a dictionary.
2. Client sends a domain query.
3. Server responds with IP or "NXDOMAIN" if not found.

---

## ⚙️ Configuration Commands

```
! ---- DNS Server Setup (Cisco Packet Tracer) ----
! On Server > Services > DNS:
! Add Record: www.cnlab.com  →  192.168.1.100
! Add Record: ftp.cnlab.com  →  192.168.1.102

! On PC > Desktop > IP Configuration:
! DNS Server: 192.168.1.200  (IP of DNS server)

! Testing DNS resolution
PC> nslookup www.cnlab.com
PC> ping www.cnlab.com
```

```python
# Simple DNS Server Simulation (Python)
import socket

dns_records = {
    "www.cnlab.com": "192.168.1.100",
    "mail.cnlab.com": "192.168.1.101",
    "ftp.cnlab.com": "192.168.1.102"
}

def dns_lookup(domain):
    return dns_records.get(domain, "NXDOMAIN")

# DNS client query
domain = "www.cnlab.com"
result = dns_lookup(domain)
print(f"DNS Query: {domain} → {result}")

# DDNS Update
def ddns_update(domain, new_ip):
    dns_records[domain] = new_ip
    print(f"DDNS Updated: {domain} → {new_ip}")

ddns_update("www.cnlab.com", "192.168.1.150")
print(f"After update: {dns_lookup('www.cnlab.com')}")
```

---

## 📊 Observations / Results

> 📷 Add output screenshots in the `screenshots/` folder.

| Domain | Queried IP | Resolved IP | Status |
|--------|-----------|-------------|--------|
| www.cnlab.com | DNS Server | 192.168.1.100 | ✅ |
| mail.cnlab.com | DNS Server | 192.168.1.101 | ✅ |
| unknown.com | DNS Server | — | NXDOMAIN |

---

## ✅ Conclusion

This experiment demonstrated DNS resolution — how domain names are mapped to IP addresses through a hierarchical system. DDNS further enables dynamic mapping, allowing devices with changing IPs to be reliably accessible via consistent hostnames.
