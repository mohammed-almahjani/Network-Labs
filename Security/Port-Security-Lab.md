# 🛡️ Port Security Lab

# 📚 Objective

Configure Port Security on a Cisco switch to restrict unauthorized devices from connecting to the network.

---

# 🛠️ Topology

- 1 Cisco Switch
- 2 PCs

---

# 🌍 Network Design

| Device | Interface | MAC Learning |
|--------|-----------|---------------|
| PC1 | Fa0/1 | Allowed |
| Unknown Device | Fa0/1 | Blocked |

---

# 🎯 Scenario

- Allow only one authorized device on a switch port.
- Automatically block unauthorized devices.

---

# ⚙️ Switch Configuration

## Step 1 — Enter Interface Configuration

```bash
enable
configure terminal

interface fastethernet 0/1
```

---

## Step 2 — Configure Access Mode

```bash
switchport mode access
```

---

## Step 3 — Enable Port Security

```bash
switchport port-security
```

---

## Step 4 — Limit Allowed MAC Addresses

```bash
switchport port-security maximum 1
```

---

## Step 5 — Configure Sticky MAC Learning

```bash
switchport port-security mac-address sticky
```

---

## Step 6 — Configure Violation Mode

```bash
switchport port-security violation shutdown
```

---

# 🔍 Verification Commands

## Verify Port Security Status

```bash
show port-security
```

---

## Verify Learned MAC Addresses

```bash
show port-security address
```

---

## Verify Interface Status

```bash
show interfaces status
```

---

# 🧪 Connectivity Testing

## Authorized Device

✅ Expected:
- PC1 connects successfully.

---

## Unauthorized Device

❌ Expected:
- Port enters shutdown state after violation.

---

# 🎯 Expected Results

- Only authorized devices can access the network.
- Unauthorized devices trigger security violations.
- Port Security protects against rogue devices.

---

# 🛡️ Security Notes

- Port Security helps prevent MAC flooding attacks.
- Sticky MAC simplifies MAC address management.
- Shutdown violation mode provides strong protection.

---

# 🧠 Troubleshooting

## Common Issues

### Port in Err-Disabled State

Possible Causes:
- Unauthorized device connected
- MAC address limit exceeded

---

## Recovery Commands

```bash
interface fastethernet 0/1
shutdown
no shutdown
```

---

## Useful Commands

```bash
show port-security
show running-config
show interfaces status
```

---

# 🌍 Real-World Usage

Port Security is widely used in:
- Enterprise Access Switches
- Office Networks
- Campus Networks
- Internal LAN Security

---

# 🧠 Skills Learned

- Port Security Configuration
- MAC Address Restriction
- Switch Hardening
- Rogue Device Prevention
- Basic LAN Security
