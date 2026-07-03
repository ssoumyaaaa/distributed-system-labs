# Cron Jobs in Linux

Cron is a time-based job scheduler in Linux used to run scripts or commands automatically at specific intervals. It is widely used for backups, monitoring, and automation in DevOps.

---

## ⏰ What is Cron?

Cron runs background jobs at scheduled times like:
- Every minute
- Daily
- Weekly
- Monthly
- Custom intervals

---

## 📌 Cron Syntax

```text
* * * * * command
│ │ │ │ │
│ │ │ │ └── Day of week (0-7)
│ │ │ └──── Month (1-12)
│ │ └────── Day of month (1-31)
│ └──────── Hour (0-23)
└────────── Minute (0-59)
```

---

## 🧰 Edit Cron Jobs

```bash
crontab -e
```

---

## 📋 View Cron Jobs

```bash
crontab -l
```

---

## ❌ Remove Cron Jobs

```bash
crontab -r
```

---

## 📌 Common Cron Examples

### Run every minute

```bash
* * * * * /path/script.sh
```

### Run daily at 2 AM

```bash
0 2 * * * /path/script.sh
```

### Run every Sunday at 3 PM

```bash
0 15 * * 0 /path/script.sh
```

### Run every 5 minutes

```bash
*/5 * * * * /path/script.sh
```

---

## 📂 System-wide Cron Jobs

File:

```bash
/etc/crontab
```

---

## 🧑‍💻 Cron Directories

| Directory | Purpose |
|----------|--------|
| /etc/cron.daily | Daily jobs |
| /etc/cron.hourly | Hourly jobs |
| /etc/cron.weekly | Weekly jobs |
| /etc/cron.monthly | Monthly jobs |

---

## 📜 Cron Logs

Check cron execution logs:

```bash
cat /var/log/syslog | grep cron
```

or

```bash
journalctl -u cron
```

---

## ⚠️ Important Notes

- Always use full paths in cron scripts
- Environment variables are limited in cron
- Check script permissions before scheduling

---

## 🧠 Key Concepts

- Cron automates tasks in Linux
- Uses time-based scheduling
- Runs in background without user interaction
- Essential for DevOps automation

---

## 🛠️ Practice

```bash
crontab -e
# Add:
* * * * * echo "Hello Cron" >> /tmp/cron.log
```

---

## 🎯 Why This Matters

- Automates backups and maintenance
- Used in CI/CD pipelines
- Critical for system monitoring tasks
- Helps reduce manual operations

---
