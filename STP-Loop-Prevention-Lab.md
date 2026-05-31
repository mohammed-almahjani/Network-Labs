# 🌳 STP Loop Prevention Lab

# 📚 Objective

Configure Spanning Tree Protocol (STP) to prevent switching loops and maintain a stable Layer 2 network.

---

# 🛠️ Topology

- 3 Cisco Switches
- Redundant Links Between Switches
- 2 PCs

---

# 🌍 Scenario

- Multiple switches are connected with redundant links.
- STP is required to prevent Layer 2 loops and broadcast storms.

---

# ⚙️ Basic Switch Configuration

## Configure Hostnames

### Switch 1

```bash
enable
configure terminal

hostname SW1
```

---

### Switch 2

```bash
enable
configure terminal

hostname SW2
```

---

### Switch 3

```bash
enable
configure terminal

hostname SW3
```

---

# 🌳 Configure Root Bridge

## Make SW1 Root Bridge

```bash
spanning-tree vlan 1 priority 4096
```

---

# 🔍 Verification Commands

## Verify STP Status

```bash
show spanning-tree
```

---

## Verify Root Bridge

```bash
show spanning-tree root
```

---

## Verify Blocked Ports

```bash
show spanning-tree blockedports
```

---

# 🧪 Connectivity Testing

✅ Expected:
- Network remains stable.
- One redundant path is blocked automatically.
- No switching loops occur.

---

# 🎯 Expected Results

- STP elects a Root Bridge.
- Redundant links are managed safely.
- Broadcast storms are prevented.

---

# 🛡️ Security Notes

- STP prevents catastrophic Layer 2 loops.
- Broadcast storms can completely crash a network.
- Root Bridge placement is important for network optimization.

---

# 🧠 Troubleshooting

## Common Issues

### Network Instability

Possible Causes:
- Incorrect STP priority
- Misconfigured trunk ports
- Physical loop without STP

---

## Useful Commands

```bash
show spanning-tree
show interfaces trunk
show running-config
```

---

# 🌍 Real-World Usage

STP is widely used in:
- Enterprise Networks
- Campus Switching
- Redundant Layer 2 Networks
- Data Center Switching

---

# 🧠 Skills Learned

- STP Configuration
- Root Bridge Election
- Loop Prevention
- Redundant Link Management
- Layer 2 Troubleshooting
