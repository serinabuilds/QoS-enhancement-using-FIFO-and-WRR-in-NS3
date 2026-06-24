# Priority-Based Queue Management for QoS Enhancement Using FIFO and WRR Scheduling in NS-3

## Overview

This project implements and compares **First-In First-Out (FIFO)** and **Weighted Round Robin (WRR)** scheduling techniques for Quality of Service (QoS) enhancement in heterogeneous network traffic using the **NS-3 Network Simulator**.

The simulation models a bottleneck router handling multiple traffic classes including:

- Voice Traffic (High Priority)
- Video Traffic (Medium Priority)
- FTP Traffic (Low Priority)

Performance is evaluated using key QoS metrics such as Throughput, Packet Delivery Ratio (PDR), Delay, Jitter, and Jain's Fairness Index.

---

## Objectives

- Design a multi-node network topology in NS-3.
- Generate heterogeneous traffic flows (Voice, Video, FTP).
- Implement FIFO scheduling.
- Implement WRR-inspired weighted traffic allocation.
- Analyze QoS performance under network congestion.
- Compare FIFO and WRR scheduling techniques.

---

## Network Topology

```text
Voice Source (Node 0) ----\
                           \
Video Source (Node 1) ------> Router (Node 3) ----> Destination (Node 4)
                           /
FTP Source (Node 2) ------/
```

### Topology Details

| Component | Description |
|------------|------------|
| Nodes | 5 |
| Router | Node 3 |
| Destination | Node 4 |
| Access Links | 10 Mbps, 2 ms |
| Bottleneck Link | 1 Mbps, 10 ms |
| Simulator | NS-3 |
| Language | C++ |

---

## Traffic Configuration

### FIFO Scenario

All traffic flows compete equally for network resources.

| Traffic Type | Protocol |
|-------------|----------|
| Voice | UDP |
| Video | UDP |
| FTP | TCP |

---

### WRR Scenario

Weighted allocation is applied to emulate WRR behavior.

| Traffic Type | Weight |
|-------------|----------|
| Voice | 5 |
| Video | 3 |
| FTP | 1 |

This prioritizes latency-sensitive traffic while maintaining fairness among competing flows.

---

## QoS Metrics Evaluated

### Throughput

Amount of successfully delivered data per unit time.

### Packet Delivery Ratio (PDR)

Percentage of packets successfully received.

### End-to-End Delay

Average packet transmission delay.

### Jitter

Variation in packet arrival times.

### Jain's Fairness Index

Measures fairness of resource allocation among flows.

\[
J = \frac{(\sum x_i)^2}{n \sum x_i^2}
\]

where:

- \(x_i\) = throughput of flow i
- \(n\) = number of flows

---

# Experimental Results

## FIFO Scheduling Results

| Metric | Value |
|----------|----------|
| Packets Sent | 5615 |
| Packets Received | 5479 |
| Throughput | 1027.44 kbps |
| PDR | 97.58 % |
| Average Delay | 1.23046 s |
| Average Jitter | 0.02358 s |
| Jain Fairness Index | 0.56419 |

---

## WRR Scheduling Results

| Metric | Value |
|----------|----------|
| Packets Sent | 5662 |
| Packets Received | 5629 |
| Throughput | 691.14 kbps |
| PDR | 99.42 % |
| Average Delay | 0.52760 s |
| Average Jitter | 0.01270 s |
| Jain Fairness Index | 0.72279 |

---

# FIFO vs WRR Comparison

| Metric | FIFO | WRR |
|----------|----------:|----------:|
| Throughput (kbps) | 1027.44 | 691.14 |
| PDR (%) | 97.58 | 99.42 |
| Delay (s) | 1.23046 | 0.52760 |
| Jitter (s) | 0.02358 | 0.01270 |
| Fairness Index | 0.56419 | 0.72279 |

---

## Key Observations

### Packet Delivery Ratio

WRR achieved a higher PDR compared to FIFO, indicating more reliable packet delivery under congestion.

### Delay

Average delay was reduced by approximately 57% using WRR scheduling.

### Jitter

WRR significantly reduced jitter, improving the quality of real-time applications such as VoIP and video streaming.

### Fairness

Jain's Fairness Index improved from 0.564 to 0.723, demonstrating better resource allocation among competing traffic flows.

### Throughput

Although aggregate throughput decreased under WRR, QoS-sensitive metrics such as delay, jitter, and packet delivery improved substantially.

---

## Tools and Technologies

- NS-3 Network Simulator
- C++
- Ubuntu (WSL)
- FlowMonitor Module
- Point-to-Point Network Model

---

## Project Workflow

```text
Topology Creation
        ↓
Traffic Generation
        ↓
FIFO Scheduling
        ↓
QoS Measurement
        ↓
WRR Scheduling
        ↓
QoS Measurement
        ↓
Performance Comparison
```

---

## Repository Structure

```text
.
├── code
│   ├── fifo_wrr_fifo.cc
│   └── fifo_wrr_wrr.cc
│
├── results
│   ├── fifo_output.png
│   └── wrr_output.png
│
├── graphs
│   ├── throughput.png
│   ├── pdr.png
│   ├── delay.png
│   ├── jitter.png
│   └── fairness.png
│
└── README.md
```

---

## Future Improvements

- Implementation of a custom WRR QueueDisc in NS-3
- Dynamic traffic prioritization
- Integration with DiffServ architecture
- Evaluation under larger network topologies
- Comparison with Priority Queueing (PQ) and WFQ

---

## Author

**Serina Sakhare**

B.Tech Electronics and Communication Engineering

Manipal Institute of Technology, Manipal

---

## Keywords

`NS3` `QoS` `FIFO` `WRR` `Computer Networks` `Network Simulation` `Traffic Scheduling` `FlowMonitor` `Delay Analysis` `Jitter Analysis` `Fairness Index`
