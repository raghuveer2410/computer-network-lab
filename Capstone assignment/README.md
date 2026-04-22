# Assignment 5: ACK-Based Communication Using ICMP Request/Reply and Extra Hops

## Objective
To understand acknowledgment-like behavior using ICMP echo request and echo reply, and to study how adding network hops affects response time and packet path.

## Setup Details
* **Task 1 (Direct Setup):** PC1 connected directly to PC2 via a single Switch.
* **Task 2 (Multi-Hop Setup):** PC1 connected to PC2 via two Switches (an extra hop inserted).

## Key Observations
Adding an extra hop (switch) introduces additional store-and-forward delay and increases the number of steps a packet takes to reach its destination. However, the ICMP request/reply mechanism handles this seamlessly, proving successful communication in both topologies.
