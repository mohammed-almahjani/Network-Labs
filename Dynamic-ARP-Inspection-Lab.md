# 🛡️ Dynamic ARP Inspection (DAI) Lab

# 📚 Objective

Configure Dynamic ARP Inspection (DAI) to prevent ARP spoofing and man-in-the-middle attacks.

---

# 🛠️ Topology

- 1 Cisco Switch
- 1 DHCP Server
- 2 PCs

---

# 🌍 Scenario

- Protect the network from fake ARP replies.
- Allow only valid ARP traffic.

---

# ⚙️ Switch Configuration

## Step 1 — Enable DHCP Snooping

```bash
enable
configure terminal

ip dhcp snooping
ip dhcp snooping vlan 10
```

---

## Step 2 — Enable Dynamic ARP Inspection

```bash
ip arp inspection vlan 10
```

---

## Step 3 — Configure Trusted Interface

```bash
interface g0/1
ip arp inspection trust
```

---

# 🔍 Verification Commands

```bash
show ip arp inspection
show ip arp inspection statistics
```

---

# 🎯 Expected Results

- Invalid ARP packets are blocked.
- Legitimate ARP traffic is allowed.

---

# 🛡️ Security Notes

- DAI protects against ARP Spoofing.
- Prevents MITM attacks in LAN environments.
- Works with DHCP Snooping bindings.

---

# 🧠 Troubleshooting

## Common Issues

- DHCP Snooping disabled
- Incorrect trusted interfaces
- Static devices without bindings

---

# 🌍 Real-World Usage

Used in:
- Enterprise Networks
- Secure Campus LANs
- Internal Network Protection

---

# 🧠 Skills Learned

- Dynamic ARP Inspection
- ARP Spoofing Prevention
- Layer 2 Security
- MITM Mitigation
