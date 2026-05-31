# 🔐 SSH Secure Access Lab

# 📚 Objective

Configure secure remote management access to a Cisco router using SSH instead of Telnet.

---

# 🛠️ Topology

- 1 Cisco Router
- 1 Switch
- 1 PC

---

# 🌍 Network Design

| Device | Interface | IP Address |
|--------|-----------|------------|
| Router | G0/0 | 192.168.1.1/24 |
| PC1 | NIC | 192.168.1.10 |

---

# 🎯 Scenario

- Enable secure remote administration using SSH.
- Disable insecure Telnet access.

---

# ⚙️ Router Configuration

## Step 1 — Configure Hostname and Domain Name

```bash
enable
configure terminal

hostname R1
ip domain-name lab.local
```

---

## Step 2 — Create Local User

```bash
username admin privilege 15 secret StrongPassword123
```

---

## Step 3 — Generate RSA Keys

```bash
crypto key generate rsa
```

### Recommended Key Size

```bash
1024
```

---

## Step 4 — Enable SSH Version 2

```bash
ip ssh version 2
```

---

## Step 5 — Configure VTY Lines

```bash
line vty 0 4
login local
transport input ssh
```

---

# 🔍 Verification Commands

## Verify SSH Status

```bash
show ip ssh
```

---

## Verify Running Configuration

```bash
show running-config
```

---

# 🧪 Connectivity Testing

## Connect Using SSH

```bash
ssh -l admin 192.168.1.1
```

✅ Expected: Successful secure login.

---

## Telnet Test

```bash
telnet 192.168.1.1
```

❌ Expected: Connection blocked.

---

# 🎯 Expected Results

- SSH remote access works successfully.
- Telnet access is disabled.
- Remote management traffic is encrypted.

---

# 🛡️ Security Notes

- SSH encrypts authentication and management traffic.
- Telnet sends credentials in plain text and should be avoided.
- Strong passwords and SSH Version 2 are recommended.

---

# 🧠 Troubleshooting

## Common Issues

### SSH Connection Failed

Possible Causes:
- RSA keys not generated
- Missing domain name
- Incorrect VTY configuration
- Interface shutdown

---

## Useful Commands

```bash
show ip ssh
show running-config
show users
```

---

# 🌍 Real-World Usage

SSH is widely used in:
- Enterprise Networks
- Data Centers
- Cloud Infrastructure
- Secure Device Management
- Remote Administration

---

# 🧠 Skills Learned

- SSH Configuration
- Secure Remote Access
- Cisco Device Hardening
- User Authentication
- Network Security Basics
