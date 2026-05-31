# 🌐 OSPF Multi-Router Lab

# 📚 Objective

Configure OSPF routing between multiple routers and verify dynamic route exchange across the network.

---

# 🛠️ Topology

- 3 Cisco Routers
- 3 LAN Networks
- Serial Connections Between Routers

---

# 🌍 Network Design

| Device | Interface | IP Address |
|--------|-----------|------------|
| R1 | G0/0 | 192.168.1.1/24 |
| R2 | G0/0 | 192.168.2.1/24 |
| R3 | G0/0 | 192.168.3.1/24 |

---

# 🔗 Router Interconnections

| Connection | Network |
|------------|---------|
| R1 ↔ R2 | 10.0.12.0/30 |
| R2 ↔ R3 | 10.0.23.0/30 |

---

# ⚙️ Basic Router Configuration

## Router 1

```bash
enable
configure terminal

hostname R1

interface g0/0
ip address 192.168.1.1 255.255.255.0
no shutdown

router ospf 1
network 192.168.1.0 0.0.0.255 area 0
network 10.0.12.0 0.0.0.3 area 0
```

---

## Router 2

```bash
enable
configure terminal

hostname R2

interface g0/0
ip address 192.168.2.1 255.255.255.0
no shutdown

router ospf 1
network 192.168.2.0 0.0.0.255 area 0
network 10.0.12.0 0.0.0.3 area 0
network 10.0.23.0 0.0.0.3 area 0
```

---

## Router 3

```bash
enable
configure terminal

hostname R3

interface g0/0
ip address 192.168.3.1 255.255.255.0
no shutdown

router ospf 1
network 192.168.3.0 0.0.0.255 area 0
network 10.0.23.0 0.0.0.3 area 0
```

---

# 🔍 Verification Commands

## Verify OSPF Neighbors

```bash
show ip ospf neighbor
```

---

## Verify Routing Table

```bash
show ip route
```

---

## Test Connectivity

```bash
ping 192.168.3.1
```

---

# 🎯 Expected Results

- All routers establish OSPF neighbor relationships.
- Dynamic routes appear in the routing table.
- Full connectivity is achieved between LANs.

---

# 🛡️ Security Notes

- OSPF reduces manual routing configuration.
- Authentication can be enabled for secure OSPF communication.

---

# 🧠 Troubleshooting

## Common Issues

### OSPF Neighbor Not Forming
Possible Causes:
- Area mismatch
- Incorrect wildcard mask
- Interface shutdown

---

## Useful Commands

```bash
show ip ospf interface
show running-config
debug ip ospf adj
```

---

# 🌍 Real-World Usage

OSPF is widely used in:
- Enterprise Networks
- ISP Infrastructure
- Campus Networks
- Large Internal Routing Environments

---

# 🧠 Skills Learned

- Dynamic Routing
- OSPF Configuration
- Route Verification
- Router Troubleshooting
- Multi-Router Communication
