# 🌐 VLAN Configuration Lab

# 📚 Objective

The purpose of this lab is to configure VLANs on a Layer 2 switch, assign switch ports to VLANs, and verify communication between devices within the same VLAN.

---

# 🛠️ Topology

- 1 Cisco Switch
- 4 PCs

---

# 🌍 VLAN Design

| VLAN ID | VLAN Name | Devices |
|----------|------------|----------|
| 10 | SALES | PC1, PC2 |
| 20 | IT | PC3, PC4 |

---

# 🌐 IP Addressing

| Device | IP Address | VLAN |
|--------|------------|------|
| PC1 | 192.168.10.10 | VLAN 10 |
| PC2 | 192.168.10.11 | VLAN 10 |
| PC3 | 192.168.20.10 | VLAN 20 |
| PC4 | 192.168.20.11 | VLAN 20 |

---

# ⚙️ Switch Configuration

## Step 1 — Enter Configuration Mode

```bash
enable
configure terminal
```

---

## Step 2 — Create VLANs

```bash
vlan 10
name SALES

vlan 20
name IT
```

---

## Step 3 — Assign Ports to VLAN 10

```bash
interface fastethernet 0/1
switchport mode access
switchport access vlan 10

interface fastethernet 0/2
switchport mode access
switchport access vlan 10
```

---

## Step 4 — Assign Ports to VLAN 20

```bash
interface fastethernet 0/3
switchport mode access
switchport access vlan 20

interface fastethernet 0/4
switchport mode access
switchport access vlan 20
```

---

# 🔍 Verification Commands

## Show VLAN Information

```bash
show vlan brief
```

---

## Test Connectivity

- Ping PC1 → PC2 ✅
- Ping PC3 → PC4 ✅
- Ping PC1 → PC3 ❌

---

# 🎯 Expected Results

- Devices inside the same VLAN can communicate successfully.
- Communication between different VLANs is blocked without inter-VLAN routing.

---

# 🛡️ Security Notes

- VLANs help isolate departments and reduce broadcast traffic.
- VLAN segmentation improves security inside enterprise networks.

---

# 🧠 Troubleshooting

## Problem:
PCs cannot communicate inside the same VLAN.

## Possible Causes:
- Wrong VLAN assignment
- Incorrect IP addressing
- Port shutdown state

## Useful Commands:

```bash
show vlan brief
show running-config
```

---

# 🌍 Real-World Usage

VLANs are widely used in enterprise networks to separate departments such as:
- HR
- IT
- Sales
- Management

---

# 🧠 Skills Learned

- VLAN Creation
- Port Assignment
- Layer 2 Segmentation
- Switch Configuration
- VLAN Verification
- Basic Troubleshooting
