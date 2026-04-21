# Experiment 9 — Transport Layer Protocols (UDP, TCP, SCTP)

**Course:** Computer Networks Lab (ENCS304)  
**Institution:** KR Mangalam University  

---

## 🎯 Aim

Implement a transport layer simulation to demonstrate process-to-process communication using UDP, TCP, and SCTP. Compare the protocols in terms of connection establishment, data transmission, and congestion control.

---

## 📌 Objective

- Understand how transport layer protocols enable process-to-process communication.
- Implement and compare UDP and TCP using socket programming.
- Understand TCP's three-way handshake and congestion control.
- Explore SCTP as a modern alternative combining features of TCP and UDP.

---

## 📖 Theory

| Feature | UDP | TCP | SCTP |
|---------|-----|-----|------|
| Connection | Connectionless | Connection-oriented | Connection-oriented |
| Reliability | ❌ No | ✅ Yes | ✅ Yes |
| Ordering | ❌ No | ✅ Yes | ✅ Yes |
| Flow Control | ❌ No | ✅ Yes | ✅ Yes |
| Congestion Control | ❌ No | ✅ Yes | ✅ Yes |
| Multi-streaming | ❌ No | ❌ No | ✅ Yes |
| Speed | Fast | Slower | Moderate |
| Use Case | DNS, Video, Gaming | HTTP, FTP, Email | VoIP, Telephony |

### TCP Three-Way Handshake
1. **SYN** — Client sends connection request
2. **SYN-ACK** — Server acknowledges
3. **ACK** — Client confirms; connection established

---

## 🖧 Network Topology

> 📷 Add screenshots below:

- `screenshots/tcp_handshake.png`
- `screenshots/udp_transmission.png`
- `screenshots/tcp_vs_udp_comparison.png`
- `screenshots/wireshark_capture.png`

---

## 🔧 Step-by-Step Procedure

### TCP Server-Client (Python)
1. Create a TCP server that listens on port 8080.
2. Create a TCP client that connects and sends a message.
3. Observe connection establishment (SYN, SYN-ACK, ACK).
4. Close connection gracefully (FIN, FIN-ACK).

### UDP Server-Client (Python)
1. Create a UDP server listening on port 9090.
2. Create a UDP client that sends datagrams.
3. Observe that no connection setup is needed.

---

## ⚙️ Configuration Commands

```python
# ---- TCP Server ----
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server.bind(('0.0.0.0', 8080))
server.listen(5)
print("TCP Server listening on port 8080...")
conn, addr = server.accept()
print(f"Connected by {addr}")
data = conn.recv(1024)
print(f"Received: {data.decode()}")
conn.sendall(b"Hello from TCP Server!")
conn.close()

# ---- TCP Client ----
client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client.connect(('127.0.0.1', 8080))
client.sendall(b"Hello from TCP Client!")
data = client.recv(1024)
print(f"Received: {data.decode()}")
client.close()

# ---- UDP Server ----
udp_server = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
udp_server.bind(('0.0.0.0', 9090))
print("UDP Server listening on port 9090...")
data, addr = udp_server.recvfrom(1024)
print(f"Received from {addr}: {data.decode()}")

# ---- UDP Client ----
udp_client = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
udp_client.sendto(b"Hello UDP!", ('127.0.0.1', 9090))
```

---

## 📊 Observations / Results

> 📷 Add output screenshots in the `screenshots/` folder.

| Protocol | Connection Setup | Data Sent | Data Received | Loss | Latency |
|----------|-----------------|-----------|---------------|------|---------|
| TCP | 3-way handshake | — | — | 0% | Higher |
| UDP | None | — | — | Possible | Lower |

---

## ✅ Conclusion

TCP provides reliable, ordered delivery at the cost of higher overhead, making it ideal for applications requiring data integrity. UDP offers lower latency with no reliability guarantees, suitable for real-time applications. SCTP combines the best features of both, with multi-streaming and multi-homing support.
