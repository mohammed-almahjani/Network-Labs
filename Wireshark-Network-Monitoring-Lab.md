# 🕵️ Wireshark Network Monitoring Lab

# 📚 Objective

Use Wireshark to capture, analyze, and troubleshoot network traffic in a simulated enterprise environment.

---

# 🏢 Real-World Scenario

A network administrator wants to:
- Monitor network traffic.
- Detect suspicious activity.
- Analyze protocols.
- Troubleshoot connectivity problems.

Wireshark is used as the primary packet analysis tool.

---

# 🛠️ Lab Environment

| Device | Role |
|--------|------|
| PC1 | Client |
| Router | Gateway |
| Wireshark PC | Monitoring Station |

---

# 🌍 Monitoring Goals

- Capture ICMP traffic.
- Analyze HTTP communication.
- Detect failed connections.
- Identify source and destination addresses.

---

# ⚙️ Lab Setup

# Step 1 — Install Wireshark

Download and install:
- Wireshark
- Npcap

---

# Step 2 — Start Packet Capture

## Select Active Interface

Examples:
- Ethernet
- Wi-Fi

---

# Step 3 — Generate Traffic

## Ping Test

```bash
ping 8.8.8.8
```

---

## Web Browsing Test

Open:
```text
https://example.com
```

---

# 🔍 Packet Analysis

# ICMP Analysis

## Filter ICMP Traffic

```text
icmp
```

---

# HTTP Analysis

## Filter HTTP Packets

```text
http
```

---

# DNS Analysis

## Filter DNS Queries

```text
dns
```

---

# TCP Troubleshooting

## Filter TCP Errors

```text
tcp.analysis.flags
```

---

# 🔬 Packet Inspection Tasks

- Identify source IP address.
- Identify destination IP address.
- Analyze protocol type.
- Inspect TCP handshake.
- Detect retransmissions.

---

# 🧪 Troubleshooting Scenarios

| Issue | Wireshark Usage |
|------|----------------|
| High Latency | Analyze RTT |
| DNS Failure | Inspect DNS Queries |
| Packet Loss | Detect Retransmissions |
| Connection Failure | Analyze TCP Handshake |

---

# 🎯 Expected Results

- Traffic is captured successfully.
- Protocols are identified correctly.
- Connectivity issues can be analyzed.
- Packet-level troubleshooting is possible.

---

# 🛡️ Security Notes

- Packet captures may contain sensitive data.
- Use monitoring tools responsibly.
- HTTPS encrypts application payloads.
- Packet analysis is essential in incident response.

---

# 🌍 Real-World Usage

Wireshark is widely used in:
- SOC Operations
- Incident Response
- Network Troubleshooting
- Security Analysis
- Malware Investigation

---

# 🧠 Skills Learned

- Packet Capture
- Protocol Analysis
- Traffic Inspection
- TCP/IP Troubleshooting
- Network Monitoring
- Security Analysis
