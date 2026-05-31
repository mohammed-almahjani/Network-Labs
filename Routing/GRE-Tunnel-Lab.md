# 🌐 GRE Tunnel Lab

# 📚 Objective

Configure a GRE Tunnel between two routers to allow communication between remote networks over an IP infrastructure.

---

# 🛠️ Topology

- Router 1
- Router 2
- Simulated WAN Connection

---

# 🌍 Network Design

| Device | Interface | IP Address |
|--------|-----------|------------|
| R1 G0/0 | LAN | 192.168.1.1/24 |
| R1 S0/0 | WAN | 10.0.0.1/30 |
| R2 G0/0 | LAN | 192.168.2.1/24 |
| R2 S0/0 | WAN | 10.0.0.2/30 |

---

# 🎯 Scenario

- Connect two remote LANs securely through a GRE tunnel.
- Encapsulate traffic between remote sites.

---

# ⚙️ Router 1 Configuration

## Configure Tunnel Interface

```bash
enable
configure terminal

interface tunnel 0
ip address 172.16.1.1 255.255.255.252
tunnel source 10.0.0.1
tunnel destination 10.0.0.2
```

---

## Configure Static Route

```bash
ip route 192.168.2.0 255.255.255.0 172.16.1.2
```

---

# ⚙️ Router 2 Configuration

## Configure Tunnel Interface

```bash
enable
configure terminal

interface tunnel 0
ip address 172.16.1.2 255.255.255.252
tunnel source 10.0.0.2
tunnel destination 10.0.0.1
```

---

## Configure Static Route

```bash
ip route 192.168.1.0 255.255.255.0 172.16.1.1
```

---

# 🔍 Verification Commands

```bash
show interface tunnel 0
show ip route
```

---

# 🧪 Connectivity Testing

```bash
ping 192.168.2.1
```

✅ Expected:
- Remote LAN communication succeeds through the GRE tunnel.

---

# 🎯 Expected Results

- GRE tunnel becomes operational.
- Remote networks communicate successfully.
- Traffic is encapsulated over the WAN.

---

# 🛡️ Security Notes

- GRE itself does not encrypt traffic.
- GRE is often combined with IPsec VPN for security.
- Tunnel interfaces simplify routing between remote sites.

---

# 🧠 Troubleshooting

## Common Issues

- Incorrect tunnel source/destination
- WAN connectivity failure
- Missing static routes

---

## Useful Commands

```bash
show interfaces tunnel 0
show ip route
show running-config
```

---

# 🌍 Real-World Usage

Used in:
- WAN Connectivity
- Site Interconnection
- Enterprise Networks
- Overlay Routing

---

# 🧠 Skills Learned

- GRE Tunnel Configuration
- Tunnel Routing
- WAN Connectivity
- Overlay Networks
- Tunnel Troubleshooting
