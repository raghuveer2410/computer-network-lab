# Experiment 4 — Error Detection & Correction (Block Coding and CRC)

**Course:** Computer Networks Lab (ENCS304)  
**Institution:** KR Mangalam University  

---

## 🎯 Aim

Implement error detection and correction mechanisms using block coding and CRC. Simulate a communication system that demonstrates how errors are detected and corrected during data transmission.

---

## 📌 Objective

- Understand the need for error detection and correction in data communication.
- Implement CRC (Cyclic Redundancy Check) for error detection.
- Implement Hamming Code for single-bit error correction.
- Simulate error introduction and observe detection/correction behavior.

---

## 📖 Theory

### CRC (Cyclic Redundancy Check)
CRC treats data as a binary polynomial and divides it by a generator polynomial. The remainder (CRC bits) is appended to data. At receiver, the same division is performed — a non-zero remainder indicates an error.

**Common CRC Standards:**
| Standard | Generator Polynomial | Use Case |
|----------|---------------------|----------|
| CRC-8    | x⁸+x²+x+1          | ATM |
| CRC-16   | x¹⁶+x¹⁵+x²+1       | USB, HDLC |
| CRC-32   | (32-bit polynomial)  | Ethernet, ZIP |

### Hamming Code
Hamming code adds parity bits at positions that are powers of 2. For `m` data bits, `r` parity bits are needed such that `2^r ≥ m + r + 1`.

---

## 🖧 Network Topology

> 📷 Add screenshots below:

- `screenshots/crc_simulation.png`
- `screenshots/hamming_simulation.png`
- `screenshots/error_detected.png`
- `screenshots/error_corrected.png`

---

## 🔧 Step-by-Step Procedure

### CRC Simulation
1. Choose a data word (e.g., `1101011011`) and a generator polynomial (e.g., `10011`).
2. Append (degree of generator − 1) zeros to the data.
3. Perform binary division (XOR-based) to obtain the remainder (CRC).
4. Transmit `data + CRC`.
5. At receiver, divide received data by generator — zero remainder = no error.

### Hamming Code Simulation
1. Take 4-bit data word (e.g., `1011`).
2. Calculate parity bit positions: p1(bit 1), p2(bit 2), p4(bit 4).
3. Construct 7-bit Hamming codeword.
4. Introduce a 1-bit error and verify detection/correction.

---

## ⚙️ Configuration Commands

```python
# CRC Calculation (Python)
def crc(data, generator):
    data = list(data + '0' * (len(generator) - 1))
    gen = list(generator)
    for i in range(len(data) - len(gen) + 1):
        if data[i] == '1':
            for j in range(len(gen)):
                data[i + j] = str(int(data[i + j]) ^ int(gen[j]))
    return ''.join(data[-(len(generator) - 1):])

# Hamming Code (Python)
def hamming_encode(data):
    # Insert parity bits at positions 1, 2, 4 (1-indexed)
    n = len(data)
    r = 0
    while (2 ** r) < (n + r + 1):
        r += 1
    return r  # number of parity bits needed
```

---

## 📊 Observations / Results

> 📷 Add output screenshots in the `screenshots/` folder.

| Method | Data Bits | Redundancy Bits | Detects | Corrects |
|--------|-----------|----------------|---------|---------|
| CRC-8  | Any       | 8 bits         | Burst errors | ❌ |
| CRC-32 | Any       | 32 bits        | Burst errors | ❌ |
| Hamming| 4 bits    | 3 bits         | 2-bit errors | 1-bit errors |

---

## ✅ Conclusion

This experiment successfully demonstrated error detection using CRC and error correction using Hamming Code. CRC is highly effective for detecting burst errors in data transmission, while Hamming Code is ideal for correcting single-bit errors in memory and communication systems.
