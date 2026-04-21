# Experiment 5 — Flow Control & ARQ Protocols (Stop-and-Wait, Go-Back-N, Selective Repeat)

**Course:** Computer Networks Lab (ENCS304)  
**Institution:** KR Mangalam University  

---

## 🎯 Aim

Design and simulate flow control and error control protocols — Stop-and-Wait, Go-Back-N ARQ, and Selective Repeat ARQ. Compare their performance in terms of throughput and efficiency under varying network conditions.

---

## 📌 Objective

- Understand the need for flow control and error control in data communication.
- Implement and simulate three ARQ protocols.
- Compare throughput and efficiency under packet loss scenarios.

---

## 📖 Theory

**ARQ (Automatic Repeat reQuest)** protocols combine error detection with retransmission to provide reliable data transfer.

| Protocol | Window Size | Retransmission Strategy | Efficiency |
|----------|------------|------------------------|------------|
| Stop-and-Wait | 1 | Retransmit single frame | Low |
| Go-Back-N | N | Retransmit from error frame onwards | Medium |
| Selective Repeat | N | Retransmit only erroneous frame | High |

### Efficiency Formulas
- **Stop-and-Wait:** η = 1 / (1 + 2a), where a = propagation delay / transmission time
- **Go-Back-N:** η = (1 − P) / (1 + 2a × P), P = error probability
- **Selective Repeat:** η = (1 − P)

---

## 🖧 Network Topology

> 📷 Add screenshots below:

- `screenshots/stop_and_wait.png`
- `screenshots/go_back_n.png`
- `screenshots/selective_repeat.png`
- `screenshots/efficiency_comparison.png`

---

## 🔧 Step-by-Step Procedure

### Stop-and-Wait
1. Sender transmits one frame and waits for ACK.
2. If ACK received → send next frame.
3. If timeout → retransmit same frame.
4. Observe one-frame-at-a-time behavior.

### Go-Back-N
1. Sender transmits up to N frames without waiting.
2. If frame i is lost/corrupted, retransmit from frame i onwards.
3. Set window size N = 7 (for 3-bit sequence numbers).

### Selective Repeat
1. Sender transmits up to N frames.
2. Only the specific lost/corrupted frame is retransmitted.
3. Receiver buffers out-of-order frames.

---

## ⚙️ Configuration Commands

```python
# Stop-and-Wait Efficiency
def stop_and_wait_efficiency(a):
    return 1 / (1 + 2 * a)

# Go-Back-N Efficiency
def go_back_n_efficiency(a, P, N):
    if N >= (1 + 2 * a):
        return (1 - P) / (1 - P + N * P)
    else:
        return N * (1 - P) / ((1 + 2 * a) * (1 - P + N * P))

# Selective Repeat Efficiency
def selective_repeat_efficiency(a, P, N):
    if N >= (1 + 2 * a):
        return 1 - P
    else:
        return N * (1 - P) / (1 + 2 * a)
```

---

## 📊 Observations / Results

> 📷 Add output screenshots in the `screenshots/` folder.

| Protocol | Window Size | Frames Sent | Frames Retransmitted | Throughput |
|----------|------------|-------------|---------------------|-----------|
| Stop-and-Wait | 1 | — | — | Low |
| Go-Back-N | 7 | — | — | Medium |
| Selective Repeat | 7 | — | — | High |

---

## ✅ Conclusion

Selective Repeat ARQ proved to be the most efficient protocol, retransmitting only erroneous frames. Go-Back-N offers a balance between complexity and performance, while Stop-and-Wait is simple but inefficient for high-latency links.
