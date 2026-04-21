# Experiment 7 — Sliding Window Protocol with Piggybacking

**Course:** Computer Networks Lab (ENCS304)  
**Institution:** KR Mangalam University  

---

## 🎯 Aim

Implement a sliding window protocol with piggybacking for efficient data transmission and error control. Simulate data transfer between two nodes and visualize the window movements and acknowledgments.

---

## 📌 Objective

- Understand the sliding window mechanism for flow control.
- Implement piggybacking to combine data and acknowledgment in a single frame.
- Visualize window movement and ACK behavior during transmission.

---

## 📖 Theory

### Sliding Window Protocol
The sliding window allows the sender to transmit multiple frames before requiring an acknowledgment. The window "slides" forward as ACKs are received.

- **Sender Window Size (SWS):** Max unacknowledged frames in transit.
- **Receiver Window Size (RWS):** Number of out-of-order frames the receiver can buffer.

### Piggybacking
Instead of sending a separate ACK frame, the receiver attaches (piggybacks) the acknowledgment onto the next outgoing data frame. This reduces overhead and improves channel utilization.

| Feature | Without Piggybacking | With Piggybacking |
|---------|---------------------|------------------|
| ACK Frame | Separate | Combined with data |
| Bandwidth | More overhead | Less overhead |
| Efficiency | Lower | Higher |

---

## 🖧 Network Topology

> 📷 Add screenshots below:

- `screenshots/sliding_window_topology.png`
- `screenshots/window_movement.png`
- `screenshots/piggybacking_demo.png`
- `screenshots/ack_visualization.png`

---

## 🔧 Step-by-Step Procedure

1. Set up a two-node simulation (Node A ↔ Node B) in Cisco Packet Tracer or Python.
2. Define window size W = 4 with 3-bit sequence numbers.
3. **Sender:** Sends frames 0, 1, 2, 3 without waiting for ACKs.
4. **Receiver:** Receives frames and sends ACKs piggybacked on data going back to sender.
5. Simulate a lost frame and observe retransmission.
6. Visualize the window sliding as ACKs arrive.

---

## ⚙️ Configuration Commands

```python
# Sliding Window Protocol Simulation (Python)

WINDOW_SIZE = 4
total_frames = 10
sent = 0
acked = 0

while acked < total_frames:
    # Send up to WINDOW_SIZE unacknowledged frames
    while sent < acked + WINDOW_SIZE and sent < total_frames:
        print(f"Sending frame {sent}")
        sent += 1

    # Simulate receiving ACK for next frame
    print(f"ACK received for frame {acked}")
    acked += 1
    print(f"Window slides: [{acked}, {acked + WINDOW_SIZE - 1}]")

# Piggybacking example
class Frame:
    def __init__(self, seq_no, data, ack_no=None):
        self.seq_no = seq_no
        self.data = data
        self.ack_no = ack_no  # Piggybacked ACK

    def __str__(self):
        return f"Frame(seq={self.seq_no}, data='{self.data}', ack={self.ack_no})"

# Node B sends data with piggybacked ACK
response = Frame(seq_no=0, data="Hello A", ack_no=3)
print(response)
```

---

## 📊 Observations / Results

> 📷 Add output screenshots in the `screenshots/` folder.

| Window Size | Frames Sent | ACKs Received | Retransmissions | Efficiency |
|-------------|------------|---------------|-----------------|-----------|
| W = 1       | 10         | 10            | —               | Low |
| W = 4       | 10         | 10            | —               | High |
| W = 4 (loss)| 10         | 9             | 1               | Medium |

---

## ✅ Conclusion

The sliding window protocol with piggybacking significantly improves network efficiency by allowing multiple in-flight frames and combining ACK transmission with outgoing data. This reduces both overhead and idle time on the communication channel.
