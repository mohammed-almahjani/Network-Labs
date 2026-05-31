# 🌐 VLAN Configuration Lab

## 📚 Objective

Configure VLANs on switches and test communication between devices inside the same VLAN.

---

# 🛠️ Topology

- 1 Switch
- 4 PCs

---

# 🌍 VLAN Design

| VLAN | Name | Devices |
|------|------|----------|
| 10 | SALES | PC1, PC2 |
| 20 | IT | PC3, PC4 |

---

# ⚙️ Switch Configuration

## Create VLANs

```bash
enable
configure terminal

vlan 10
name SALES

vlan 20
name IT
```

---

# ⚙️ Assign Ports to VLANs

```bash
interface fastethernet 0/1
switchport mode access
switchport access vlan 10

interface fastethernet 0/2
switchport mode access
switchport access vlan 10

interface fastethernet 0/3
switchport mode access
switchport access vlan 20

interface fastethernet 0/4
switchport mode access
switchport access vlan 20
```

---

# 🔍 Verification Commands

```bash
show vlan brief
```

---

# 🎯 Result

- PCs inside the same VLAN can communicate successfully.
- Communication between different VLANs is blocked without routing.

---

# 🧠 Skills Learned

- VLAN Creation
- Port Assignment
- Switch Configuration
- Network Segmentation
- VLAN Verification
