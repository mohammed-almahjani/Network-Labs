# 🌐 OSPF Lab

## 📚 Objective

Configure OSPF routing between routers and verify network connectivity.

---

# 🛠️ Topology

- Router1
- Router2
- Router3

---

# ⚙️ IP Addressing

| Device | Interface | IP Address |
|--------|-----------|------------|
| R1 | G0/0 | 192.168.1.1/24 |
| R2 | G0/0 | 192.168.2.1/24 |
| R3 | G0/0 | 192.168.3.1/24 |

---

# ⚙️ OSPF Configuration

## Router 1

```bash
enable
configure terminal

router ospf 1
network 192.168.1.0 0.0.0.255 area 0
```

## Router 2

```bash
enable
configure terminal

router ospf 1
network 192.168.2.0 0.0.0.255 area 0
```

## Router 3

```bash
enable
configure terminal

router ospf 1
network 192.168.3.0 0.0.0.255 area 0
```

---

# 🔍 Verification Commands

```bash
show ip ospf neighbor
show ip route
```

---

# 🎯 Result

All routers successfully exchanged routing information using OSPF.

---

# 🧠 Skills Learned

- OSPF Configuration
- Dynamic Routing
- Router Communication
- Route Verification
