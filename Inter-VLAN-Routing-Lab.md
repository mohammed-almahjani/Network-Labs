# 🌐 Inter-VLAN Routing Lab

# 📚 Objective

Configure Inter-VLAN Routing using Router-on-a-Stick to allow communication between multiple VLANs.

---

# 🛠️ Topology

- 1 Cisco Router
- 1 Cisco Switch
- 4 PCs

---

# 🌍 VLAN Design

| VLAN ID | Name | Devices |
|----------|------|----------|
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

## Step 1 — Create VLANs

```bash
enable
configure terminal

vlan 10
name SALES

vlan 20
name IT
```

---

## Step 2 — Assign Access Ports

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

## Step 3 — Configure Trunk Port

```bash
interface fastethernet 0/24
switchport mode trunk
```

---

# ⚙️ Router Configuration

## Step 1 — Configure Subinterfaces

```bash
enable
configure terminal

interface g0/0
no shutdown
```

---

## VLAN 10 Subinterface

```bash
interface g0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
```

---

## VLAN 20 Subinterface

```bash
interface g0/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
```

---

# 🔍 Verification Commands

## Verify VLANs

```bash
show vlan brief
```

---

## Verify Trunking

```bash
show interfaces trunk
```

---

## Verify Router Interfaces

```bash
show ip interface brief
```

---

# 🧪 Connectivity Testing

## Ping Between VLANs

```bash
ping 192.168.20.10
```

✅ Expected:
- Successful communication between VLANs.

---

# 🎯 Expected Results

- Devices in different VLANs can communicate successfully.
- Router performs Layer 3 routing between VLANs.
- Trunk link carries traffic for multiple VLANs.

---

# 🛡️ Security Notes

- VLAN segmentation improves network organization and security.
- Trunk ports should be restricted to required VLANs only.
- Inter-VLAN Routing centralizes traffic control.

---

# 🧠 Troubleshooting

## Common Issues

### VLANs Cannot Communicate

Possible Causes:
- Incorrect encapsulation
- Trunk misconfiguration
- Wrong VLAN assignment
- Subinterface shutdown

---

## Useful Commands

```bash
show interfaces trunk
show vlan brief
show running-config
```

---

# 🌍 Real-World Usage

Inter-VLAN Routing is widely used in:
- Enterprise Networks
- Office Infrastructure
- Campus Networks
- Department Segmentation

---

# 🧠 Skills Learned

- VLAN Configuration
- Router-on-a-Stick
- Trunk Configuration
- Layer 3 Routing
- VLAN Troubleshooting
