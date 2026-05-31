# ⚡ EtherChannel Lab

# 📚 Objective

Configure EtherChannel between switches to combine multiple physical links into a single logical connection for redundancy and increased bandwidth.

---

# 🛠️ Topology

- 2 Cisco Switches
- 2 Physical Links Between Switches
- 2 PCs

---

# 🌍 Scenario

- Multiple links exist between switches.
- EtherChannel is used to prevent STP blocking and improve bandwidth utilization.

---

# ⚙️ Switch Configuration

# Configure Switch 1

## Step 1 — Select Interfaces

```bash
enable
configure terminal

interface range fastethernet 0/1 - 2
```

---

## Step 2 — Configure Trunking

```bash
switchport mode trunk
```

---

## Step 3 — Configure EtherChannel Using LACP

```bash
channel-group 1 mode active
```

---

## Step 4 — Configure Port-Channel Interface

```bash
interface port-channel 1
switchport mode trunk
```

---

# ⚙️ Configure Switch 2

## Step 1 — Select Interfaces

```bash
enable
configure terminal

interface range fastethernet 0/1 - 2
```

---

## Step 2 — Configure Trunking

```bash
switchport mode trunk
```

---

## Step 3 — Configure EtherChannel Using LACP

```bash
channel-group 1 mode active
```

---

## Step 4 — Configure Port-Channel Interface

```bash
interface port-channel 1
switchport mode trunk
```

---

# 🔍 Verification Commands

## Verify EtherChannel Summary

```bash
show etherchannel summary
```

---

## Verify Port-Channel Interface

```bash
show interfaces port-channel 1
```

---

## Verify Trunk Status

```bash
show interfaces trunk
```

---

# 🧪 Connectivity Testing

✅ Expected:
- Both links operate as one logical connection.
- Traffic continues even if one physical link fails.

---

# 🎯 Expected Results

- EtherChannel successfully bundles physical interfaces.
- Redundancy and bandwidth are improved.
- STP sees EtherChannel as one logical link.

---

# 🛡️ Security Notes

- EtherChannel helps reduce STP blocked ports.
- Misconfigured EtherChannel can cause network instability.
- LACP is preferred for dynamic negotiation.

---

# 🧠 Troubleshooting

## Common Issues

### EtherChannel Not Forming

Possible Causes:
- Different interface configurations
- Speed/duplex mismatch
- Different trunk settings
- Different channel-group modes

---

## Useful Commands

```bash
show etherchannel summary
show running-config
show interfaces trunk
```

---

# 🌍 Real-World Usage

EtherChannel is widely used in:
- Enterprise Networks
- Data Centers
- Core Switching
- High Availability Networks

---

# 🧠 Skills Learned

- EtherChannel Configuration
- LACP Configuration
- Link Aggregation
- Redundancy Design
- Switch Troubleshooting
