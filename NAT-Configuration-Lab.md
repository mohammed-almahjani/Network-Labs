# 🌐 NAT Configuration Lab

# 📚 Objective

Configure Network Address Translation (NAT) to allow internal private networks to access external networks using a public IP address.

---

# 🛠️ Topology

- 1 Cisco Router
- 1 Internal LAN
- 1 Simulated Internet Network
- 2 PCs

---

# 🌍 Network Design

| Device | Interface | IP Address |
|--------|-----------|------------|
| R1 G0/0 | Inside | 192.168.1.1/24 |
| R1 G0/1 | Outside | 200.1.1.1/24 |
| PC1 | NIC | 192.168.1.10 |
| PC2 | NIC | 192.168.1.11 |

---

# 🎯 Scenario

- Internal devices use private IP addresses.
- NAT translates private IPs into a public IP for internet access.

---

# ⚙️ Router Configuration

## Step 1 — Configure Interfaces

```bash
enable
configure terminal

interface g0/0
ip address 192.168.1.1 255.255.255.0
ip nat inside
no shutdown

interface g0/1
ip address 200.1.1.1 255.255.255.0
ip nat outside
no shutdown
```

---

## Step 2 — Configure Access List

```bash
access-list 1 permit 192.168.1.0 0.0.0.255
```

---

## Step 3 — Configure NAT Overload (PAT)

```bash
ip nat inside source list 1 interface g0/1 overload
```

---

# 🔍 Verification Commands

## Verify NAT Translations

```bash
show ip nat translations
```

---

## Verify NAT Statistics

```bash
show ip nat statistics
```

---

# 🧪 Connectivity Testing

```bash
ping 8.8.8.8
```

✅ Expected: Successful connectivity to external network.

---

# 🎯 Expected Results

- Internal devices can access external networks.
- Private IP addresses are translated successfully.
- NAT overload allows multiple devices to share one public IP.

---

# 🛡️ Security Notes

- NAT hides internal private addresses from external networks.
- PAT improves IP address utilization.
- NAT adds a basic layer of network privacy.

---

# 🧠 Troubleshooting

## Common Issues

### No Internet Connectivity

Possible Causes:
- Incorrect NAT inside/outside assignment
- Missing ACL
- Interface shutdown
- Incorrect default route

---

## Useful Commands

```bash
show ip nat translations
show ip interface brief
show running-config
```

---

# 🌍 Real-World Usage

NAT is widely used in:
- Enterprise Networks
- Home Routers
- ISP Networks
- Firewalls
- Internet Edge Devices

---

# 🧠 Skills Learned

- NAT Configuration
- PAT (Overload)
- Private/Public IP Translation
- Internet Connectivity
- NAT Troubleshooting
