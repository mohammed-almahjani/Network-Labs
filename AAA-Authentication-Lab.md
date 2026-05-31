# 🔐 AAA Authentication Lab

# 📚 Objective

Configure AAA Authentication on Cisco devices to centralize and secure administrative access.

---

# 🛠️ Topology

- 1 Cisco Router
- 1 Admin PC

---

# 🌍 Scenario

- Secure device login using AAA.
- Require authenticated administrative access.

---

# ⚙️ Router Configuration

## Step 1 — Enable AAA

```bash
enable
configure terminal

aaa new-model
```

---

## Step 2 — Create Local User

```bash
username admin privilege 15 secret StrongPassword123
```

---

## Step 3 — Configure AAA Authentication

```bash
aaa authentication login default local
```

---

## Step 4 — Configure Console Access

```bash
line console 0
login authentication default
```

---

## Step 5 — Configure VTY Access

```bash
line vty 0 4
login authentication default
transport input ssh
```

---

# 🔍 Verification Commands

```bash
show running-config
show users
```

---

# 🎯 Expected Results

- Administrative access requires authentication.
- Unauthorized users cannot access the device.
- AAA centralizes login control.

---

# 🛡️ Security Notes

- AAA improves accountability and access management.
- SSH should always be preferred over Telnet.
- Strong credentials are essential.

---

# 🧠 Troubleshooting

## Common Issues

- Missing local user
- Incorrect authentication method
- SSH not configured properly

---

# 🌍 Real-World Usage

Used in:
- Enterprise Networks
- Secure Infrastructure
- Device Administration
- Access Control Systems

---

# 🧠 Skills Learned

- AAA Configuration
- Administrative Security
- Cisco Access Control
- Authentication Management
