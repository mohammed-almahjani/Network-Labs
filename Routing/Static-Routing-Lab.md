# 🌐 Static Routing Lab

## 📚 Objective

Configure static routes between routers and verify connectivity between different networks.

---

# 🛠️ Topology

- Router1
- Router2
- 2 PCs

---

# 🌍 Network Design

| Device | Interface | IP Address |
|--------|-----------|------------|
| R1 | G0/0 | 192.168.1.1/24 |
| R2 | G0/0 | 192.168.2.1/24 |

---

# ⚙️ Router Configuration

## Router 1

```bash
enable
configure terminal

ip route 192.168.2.0 255.255.255.0 10.0.0.2
```

---

## Router 2

```bash
enable
configure terminal

ip route 192.168.1.0 255.255.255.0 10.0.0.1
```

---

# 🔍 Verification Commands

```bash
show ip route
ping 192.168.2.1
```

---

# 🎯 Result

Routers successfully communicated using static routing.

---

# 🧠 Skills Learned

- Static Routing
- Router Configuration
- Route Verification
- Network Connectivity Testing
