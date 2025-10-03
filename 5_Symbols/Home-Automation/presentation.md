---
marp: true
theme: default
style: |
  h1 {
    color: #007bff; /* blue */
  }
  h2 {
    color: #fd7e14; /* orange */
  }
---

# 🛡️ turn on and off home internet access for the network `192.168.3.0/24` using VyOS/EdgeOS firewall rules, scheduled via n8n workflow automation, with Telegram notifications
# 🛡️ Internet Control Automation

### Automated Internet Access Control for `192.168.3.0/24` using VyOS/EdgeOS, n8n, and Telegram.

---

## 🎯 Objective

Create an automated system to control internet access for a specific network using firewall rules, scheduled via n8n, with status notifications sent to Telegram.

---

## 🏗️ System Architecture

A simple, robust flow:

**n8n Schedule Trigger → SSH to Router → Configure Firewall → Send Telegram Notification**

- **VyOS/EdgeOS Router**: The firewall controlling traffic.
- **n8n**: The automation brain for scheduling.
- **SSH**: The communication link to the router.
- **Telegram**: The notification channel.

---

## 🔧 How It Works: The Core Logic

The entire system is based on enabling or disabling a single firewall `DROP` rule (Rule 12).

**When Rule 12 is DISABLED:**
- The `DROP` rule is inactive.
- Traffic flows normally.
- **Result: Internet is ON** ✅

**When Rule 12 is ENABLED:**
- The `DROP` rule is active.
- Traffic is blocked.
- **Result: Internet is OFF** ❌

---

## 🔄 Daily Workflow Schedule

- **5:00 AM** - Internet turns **ON**
- **8:00 PM (20:00)** - Internet turns **OFF**

This provides 15 hours of internet access per day.

---

## ⚙️ Workflow Steps: Turn Internet ON (5 AM)

1.  **Schedule Trigger** fires at 5:00 AM.
2.  **SSH Node** ensures Firewall Rule 12 exists.
3.  **SSH Node** runs `set firewall rule 12 disable`.
    - This **disables** the `DROP` rule, allowing traffic.
4.  **Telegram Node** sends "🟢 Internet turned ON" notification.

---

## ⚙️ Workflow Steps: Turn Internet OFF (8 PM)

1.  **Schedule Trigger** fires at 8:00 PM.
2.  **SSH Node** ensures Firewall Rule 12 exists.
3.  **SSH Node** runs `delete firewall rule 12 disable`.
    - This **enables** the `DROP` rule, blocking traffic.
4.  **Telegram Node** sends "🔴 Internet turned OFF" notification.

---

## 🛠️ Technical Deep Dive: SSH Commands

The magic is in the `vyatta-cfg-cmd-wrapper` which manages the configuration session.

**To Turn Internet ON (Disable the DROP rule):**
```bash
sg vyattacfg -c "
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper begin && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper set firewall name INTERNET_CONTROL rule 12 disable && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper commit && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper save && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper end
"
```

---

## ✅ Key Features

- **Automatic Rule Creation**: Self-heals by creating the firewall rule if it's missing.
- **Idempotent**: Safe to run multiple times without causing issues.
- **Status Notifications**: Clear Telegram alerts for success or failure.
- **Persistent Configuration**: Changes are saved to the router's config.
- **Fully Automated**: No manual intervention needed.

---

## 📝 Summary

This solution provides robust, automated parental controls or network scheduling.

- **Granted at 5 AM** (15 hours of access)
- **Revoked at 8 PM** (9 hours of no access)

The system is self-maintaining, resilient, and provides a clear audit trail through Telegram notifications.
