# 🛡️ DHCP Snooping Lab

# 📚 Objective

Configure DHCP Snooping to protect the network from rogue DHCP servers and unauthorized DHCP responses.

---

# 🛠️ Topology

- 2 Cisco Switches
- 1 Legitimate DHCP Server
- 1 Rogue DHCP Device
- 2 PCs

---

# 🌍 Scenario

- Only trusted ports should send DHCP replies.
- Rogue DHCP servers must be blocked.

---

# ⚙️ Switch Configuration

## Step 1 — Enable DHCP Snooping

```bash
enable
configure terminal

ip dhcp snooping
```

---

## Step 2 — Enable DHCP Snooping on VLAN

```bash
ip dhcp snooping vlan 10
```

---

## Step 3 — Configure Trusted Interface

```bash
interface g0/1
ip dhcp snooping trust
```

---

## Step 4 — Configure Untrusted Access Ports

```bash
interface range f0/1 - 24
ip dhcp snooping limit rate 10
```

---

# 🔍 Verification Commands

```bash
show ip dhcp snooping
show ip dhcp snooping binding
```

---

# 🎯 Expected Results

- Legitimate DHCP traffic is allowed.
- Rogue DHCP responses are blocked.

---

# 🛡️ Security Notes

- DHCP Snooping prevents fake DHCP attacks.
- Creates a trusted DHCP environment.
- Foundation for Dynamic ARP Inspection.

---

# 🧠 Troubleshooting

## Common Issues

- Trusted port misconfiguration
- VLAN mismatch
- DHCP server connected to untrusted port

---

# 🌍 Real-World Usage

Used in:
- Enterprise LANs
- Campus Networks
- Access Layer Security

---

# 🧠 Skills Learned

- DHCP Snooping
- Layer 2 Security
- Rogue DHCP Prevention
- Trusted Interface Design
