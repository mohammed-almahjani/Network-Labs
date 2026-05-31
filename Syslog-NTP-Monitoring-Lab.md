# 🕒 Syslog & NTP Monitoring Lab

# 📚 Objective

Configure Syslog and NTP services to improve monitoring, logging, and time synchronization across network devices.

---

# 🛠️ Topology

- 1 Cisco Router
- 1 Syslog Server
- 1 NTP Server

---

# 🌍 Scenario

- Centralize device logs.
- Synchronize device time for accurate monitoring and troubleshooting.

---

# ⚙️ Router Configuration

## Step 1 — Configure Syslog Server

```bash
enable
configure terminal

logging 192.168.1.100
logging trap informational
```

---

## Step 2 — Configure NTP Server

```bash
ntp server 192.168.1.200
```

---

## Step 3 — Configure Timezone

```bash
clock timezone UTC 0
```

---

# 🔍 Verification Commands

## Verify Logging

```bash
show logging
```

---

## Verify NTP Status

```bash
show ntp status
show ntp associations
```

---

# 🎯 Expected Results

- Logs are forwarded to the Syslog server.
- Device time is synchronized using NTP.
- Accurate timestamps appear in logs.

---

# 🛡️ Security Notes

- Accurate time is critical for incident investigations.
- Centralized logging improves visibility and auditing.
- Syslog helps detect suspicious activities.

---

# 🧠 Troubleshooting

## Common Issues

- Incorrect Syslog server IP
- NTP server unreachable
- Firewall blocking UDP ports

---

## Useful Ports

| Service | Port |
|---------|------|
| Syslog | UDP 514 |
| NTP | UDP 123 |

---

# 🌍 Real-World Usage

Used in:
- Security Monitoring
- SOC Environments
- Enterprise Infrastructure
- Incident Response

---

# 🧠 Skills Learned

- Syslog Configuration
- NTP Configuration
- Centralized Monitoring
- Time Synchronization
- Network Logging
