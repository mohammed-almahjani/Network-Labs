# 🔐 Site-to-Site VPN Lab

# 📚 Objective

Configure a Site-to-Site IPsec VPN between two routers to securely connect remote networks over the internet.

---

# 🛠️ Topology

- Router 1
- Router 2
- Simulated Internet Connection

---

# 🌍 Scenario

- Encrypt traffic between two remote offices.
- Secure communication over untrusted networks.

---

# 🌐 Network Design

| Device | Interface | IP Address |
|--------|-----------|------------|
| R1 LAN | G0/0 | 192.168.1.1/24 |
| R1 WAN | S0/0 | 10.0.0.1/30 |
| R2 LAN | G0/0 | 192.168.2.1/24 |
| R2 WAN | S0/0 | 10.0.0.2/30 |

---

# ⚙️ Step 1 — Configure ISAKMP Policy

## Router 1

```bash
crypto isakmp policy 10
encryption aes
hash sha
authentication pre-share
group 2
```

---

## Configure Pre-Shared Key

```bash
crypto isakmp key VPNKEY address 10.0.0.2
```

---

# ⚙️ Step 2 — Configure IPsec Transform Set

```bash
crypto ipsec transform-set VPN-SET esp-aes esp-sha-hmac
```

---

# ⚙️ Step 3 — Configure Access List

```bash
access-list 100 permit ip 192.168.1.0 0.0.0.255 192.168.2.0 0.0.0.255
```

---

# ⚙️ Step 4 — Create Crypto Map

```bash
crypto map VPN-MAP 10 ipsec-isakmp
set peer 10.0.0.2
set transform-set VPN-SET
match address 100
```

---

# ⚙️ Step 5 — Apply Crypto Map

```bash
interface s0/0
crypto map VPN-MAP
```

---

# 🔍 Verification Commands

```bash
show crypto isakmp sa
show crypto ipsec sa
```

---

# 🧪 Connectivity Testing

```bash
ping 192.168.2.1
```

✅ Expected:
- Traffic is encrypted successfully between sites.

---

# 🎯 Expected Results

- VPN tunnel establishes successfully.
- Traffic between sites is encrypted.
- Remote offices communicate securely.

---

# 🛡️ Security Notes

- IPsec protects confidentiality and integrity.
- AES encryption provides strong security.
- VPNs are essential for secure remote connectivity.

---

# 🧠 Troubleshooting

## Common Issues

- Pre-shared key mismatch
- Incorrect ACL configuration
- Crypto map not applied
- WAN connectivity failure

---

## Useful Commands

```bash
show crypto isakmp sa
show crypto ipsec sa
show running-config
```

---

# 🌍 Real-World Usage

Used in:
- Branch Office Connectivity
- Enterprise WAN Security
- Secure Remote Communication
- Hybrid Infrastructure

---

# 🧠 Skills Learned

- IPsec VPN Configuration
- Site-to-Site Security
- Tunnel Encryption
- WAN Security
- VPN Troubleshooting
