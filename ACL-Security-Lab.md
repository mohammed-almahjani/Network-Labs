# 🛡️ ACL Security Lab

# 📚 Objective

Configure Access Control Lists (ACLs) to control network traffic and restrict unauthorized communication between networks.

---

# 🛠️ Topology

- 2 Cisco Routers
- 2 LAN Networks
- 2 PCs

---

# 🌍 Network Design

| Device | Interface | IP Address |
|--------|-----------|------------|
| R1 | G0/0 | 192.168.1.1/24 |
| R2 | G0/0 | 192.168.2.1/24 |
| PC1 | NIC | 192.168.1.10 |
| PC2 | NIC | 192.168.2.10 |

---

# 🎯 Scenario

- Allow PC1 network to access R2.
- Deny ICMP (Ping) traffic from PC2 network to R1 network.

---

# ⚙️ Router Configuration

## Step 1 — Configure Standard ACL

```bash
enable
configure terminal

access-list 10 deny 192.168.2.0 0.0.0.255
access-list 10 permit any
```

---

## Step 2 — Apply ACL to Interface

```bash
interface g0/0
ip access-group 10 in
```

---

# 🔍 Verification Commands

## Verify ACL Configuration

```bash
show access-lists
```

---

## Verify Interface ACL Application

```bash
show running-config
```

---

# 🧪 Connectivity Testing

## Allowed Traffic

```bash
ping 192.168.2.1
```

✅ Expected: Success

---

## Blocked Traffic

```bash
ping 192.168.1.1
```

❌ Expected: Blocked

---

# 🎯 Expected Results

- Unauthorized traffic is blocked.
- Allowed traffic passes successfully.
- Network access control is enforced.

---

# 🛡️ Security Notes

- ACLs are fundamental for traffic filtering and network security.
- Incorrect ACL placement may block legitimate traffic.
- Standard ACLs filter traffic based on source IP addresses.

---

# 🧠 Troubleshooting

## Common Issues

### Traffic Blocked Unexpectedly

Possible Causes:
- ACL applied to wrong interface
- Incorrect wildcard mask
- ACL order issue

---

## Useful Commands

```bash
show access-lists
show ip interface
show running-config
```

---

# 🌍 Real-World Usage

ACLs are widely used in:
- Enterprise Networks
- Firewalls
- Access Restrictions
- Traffic Filtering
- Network Segmentation

---

# 🧠 Skills Learned

- ACL Configuration
- Traffic Filtering
- Network Security Basics
- Access Control
- Troubleshooting ACL Rules
