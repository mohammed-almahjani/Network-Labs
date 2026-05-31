# 🛡️ VLAN Hopping Prevention Lab

# 📚 Objective

Secure switch ports and trunk links to prevent VLAN Hopping attacks in a Layer 2 environment.

---

# 🛠️ Topology

- 2 Cisco Switches
- 2 PCs
- Trunk Link Between Switches

---

# 🌍 Scenario

- Prevent unauthorized VLAN access.
- Secure unused ports and trunk configurations.

---

# ⚙️ Switch Configuration

## Step 1 — Disable DTP Negotiation

```bash
enable
configure terminal

interface g0/1
switchport mode trunk
switchport nonegotiate
```

---

## Step 2 — Change Native VLAN

```bash
vlan 999
name NATIVE_BLACKHOLE

interface g0/1
switchport trunk native vlan 999
```

---

## Step 3 — Disable Unused Ports

```bash
interface range f0/10 - 24
shutdown
```

---

## Step 4 — Assign Unused Ports to Blackhole VLAN

```bash
interface range f0/10 - 24
switchport mode access
switchport access vlan 999
```

---

# 🔍 Verification Commands

```bash
show interfaces trunk
show vlan brief
show running-config
```

---

# 🎯 Expected Results

- Unauthorized VLAN hopping attempts are prevented.
- Native VLAN misuse is reduced.
- Unused ports are secured.

---

# 🛡️ Security Notes

- VLAN hopping can bypass network segmentation.
- Disable DTP whenever dynamic trunking is unnecessary.
- Always use an unused native VLAN.

---

# 🧠 Troubleshooting

## Common Issues

- Native VLAN mismatch
- Trunk negotiation enabled accidentally
- Unsecured unused ports

---

# 🌍 Real-World Usage

Used in:
- Enterprise Switch Security
- Campus LAN Protection
- Layer 2 Hardening

---

# 🧠 Skills Learned

- VLAN Security
- Trunk Hardening
- DTP Prevention
- Layer 2 Attack Mitigation
