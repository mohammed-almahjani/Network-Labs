# 🧱 Firewall Basics Lab

# 📚 Objective

Configure basic firewall filtering rules to protect internal networks from unauthorized access and control traffic flow between trusted and untrusted zones.

---

# 🏢 Real-World Scenario

A company wants to:
- Allow internal users to access the internet.
- Block unauthorized inbound traffic.
- Restrict specific services for security purposes.

The firewall is deployed at the network edge between the internal LAN and the external network.

---

# 🛠️ Topology

| Device | Role |
|--------|------|
| R1 | Firewall Router |
| SW1 | Internal Switch |
| PC1 | Internal Client |
| Internet Cloud | External Network |

---

# 🌍 Network Design

| Interface | Zone | IP Address |
|-----------|------|------------|
| G0/0 | Inside | 192.168.10.1/24 |
| G0/1 | Outside | 200.1.1.1/24 |

---

# 🔐 Security Goals

- Allow outbound web traffic.
- Block inbound ICMP traffic.
- Restrict unauthorized external access.
- Monitor denied traffic.

---

# ⚙️ Full Configuration

# Step 1 — Configure Interfaces

## Inside Interface

```bash
enable
configure terminal

interface g0/0
description INSIDE_NETWORK
ip address 192.168.10.1 255.255.255.0
no shutdown
```

---

## Outside Interface

```bash
interface g0/1
description INTERNET_CONNECTION
ip address 200.1.1.1 255.255.255.0
no shutdown
```

---

# Step 2 — Configure ACL Rules

## Create Firewall ACL

```bash
ip access-list extended FIREWALL-IN

remark Allow HTTP
permit tcp any any eq 80

remark Allow HTTPS
permit tcp any any eq 443

remark Deny ICMP Ping
deny icmp any any

remark Allow Established Sessions
permit tcp any any established

remark Log All Other Traffic
deny ip any any log
```

---

# Step 3 — Apply ACL to Outside Interface

```bash
interface g0/1
ip access-group FIREWALL-IN in
```

---

# 🔍 Verification Commands

## Verify ACLs

```bash
show access-lists
```

---

## Verify Interface ACL Assignment

```bash
show running-config interface g0/1
```

---

## Verify Active Connections

```bash
show ip interface
```

---

# 🧪 Testing Scenarios

| Test | Expected Result |
|------|-----------------|
| HTTP Traffic | Allowed |
| HTTPS Traffic | Allowed |
| ICMP Ping | Blocked |
| Unauthorized Ports | Blocked |

---

# 🎯 Expected Results

- Internet browsing functions correctly.
- ICMP traffic is blocked.
- Unauthorized traffic is denied and logged.
- Firewall policies are enforced successfully.

---

# 🛡️ Security Notes

- ACLs provide basic firewall filtering.
- Logging denied traffic improves monitoring.
- Inbound filtering reduces attack surface.
- Firewalls should follow least privilege principles.

---

# 🧠 Troubleshooting

# Common Issues

## Internet Access Not Working

Possible Causes:
- ACL blocking outbound traffic
- Incorrect interface assignment
- Missing default route

---

## ACL Not Filtering

Possible Causes:
- ACL applied in wrong direction
- Wrong interface
- Incorrect ACL order

---

# Useful Commands

```bash
show access-lists
show running-config
show ip interface brief
debug ip packet
```

---

# 🌍 Real-World Usage

Firewall filtering is widely used in:
- Enterprise Edge Routers
- Branch Offices
- ISP Customer Networks
- Security Zones
- DMZ Environments

---

# 🧠 Skills Learned

- Firewall Filtering
- ACL Security
- Traffic Inspection
- Inbound Filtering
- Security Monitoring
- Edge Protection
