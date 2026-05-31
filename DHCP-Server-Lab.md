# 🌐 DHCP Server Configuration Lab

# 📚 Objective

Configure a router as a DHCP server to automatically assign IP addresses to client devices.

---

# 🛠️ Topology

- 1 Cisco Router
- 1 Switch
- 2 PCs

---

# 🌍 Network Design

| Device | Interface | IP Address |
|--------|-----------|------------|
| Router | G0/0 | 192.168.10.1/24 |
| PC1 | DHCP | Automatic |
| PC2 | DHCP | Automatic |

---

# ⚙️ Router Configuration

## Step 1 — Enter Configuration Mode

```bash
enable
configure terminal
```

---

## Step 2 — Configure Interface

```bash
interface g0/0
ip address 192.168.10.1 255.255.255.0
no shutdown
```

---

## Step 3 — Exclude Reserved Addresses

```bash
ip dhcp excluded-address 192.168.10.1 192.168.10.10
```

---

## Step 4 — Create DHCP Pool

```bash
ip dhcp pool OFFICE

network 192.168.10.0 255.255.255.0
default-router 192.168.10.1
dns-server 8.8.8.8
```

---

# 🔍 Verification Commands

## Verify DHCP Pool

```bash
show ip dhcp pool
```

---

## Verify DHCP Bindings

```bash
show ip dhcp binding
```

---

# 🎯 Expected Results

- PCs automatically receive IP addresses from the DHCP server.
- Devices can communicate successfully within the network.

---

# 🛡️ Security Notes

- Excluding important IP addresses prevents conflicts.
- DHCP simplifies network management in enterprise environments.

---

# 🧠 Troubleshooting

## Common Issues

### PCs Not Receiving IP Addresses

Possible Causes:
- Interface shutdown
- Incorrect network statement
- DHCP service disabled

---

## Useful Commands

```bash
show running-config
show ip interface brief
```

---

# 🌍 Real-World Usage

DHCP is widely used in:
- Office Networks
- Enterprise Environments
- Home Networks
- ISP Customer Networks

---

# 🧠 Skills Learned

- DHCP Configuration
- IP Address Management
- Router Services
- Network Automation
- DHCP Troubleshooting
