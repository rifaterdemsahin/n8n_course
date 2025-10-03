# Internet Control Automation - Project Report

## 🎯 Objective
Create an automated system to control internet access for the network `192.168.3.0/24` using VyOS/EdgeOS firewall rules, scheduled via n8n workflow automation, with Telegram notifications.

---

## 📋 What We Built

### System Architecture
```
n8n Schedule Trigger → SSH to Router → Configure Firewall → Send Telegram Notification
```

### Components:
1. **VyOS/EdgeOS Router** - Firewall that controls network traffic
2. **n8n Automation Platform** - Schedules and executes tasks
3. **SSH Connection** - Communicates with router
4. **Telegram Bot** - Sends status notifications

---

## 🔧 How It Works

### The Firewall Rule (Rule 12)
```bash
Rule 12 Configuration:
- Action: DROP (blocks traffic)
- Source: 192.168.3.0/24 (your controlled network)
- Destination: 0.0.0.0/0 (all internet destinations)
- Description: "Internet control schedule"
```

### The Logic (This is Critical!)

**When Rule 12 is DISABLED:**
- The DROP rule is inactive
- Traffic from 192.168.3.0/24 flows normally
- **Result: Internet is ON** ✅

**When Rule 12 is ENABLED (active):**
- The DROP rule activates
- Traffic from 192.168.3.0/24 is blocked
- **Result: Internet is OFF** ❌

---

## 🔄 Workflow Details

### Daily Schedule:
- **5:00 AM** - Internet turns ON
- **8:00 PM (20:00)** - Internet turns OFF
- **Duration**: 15 hours of internet access per day

### Workflow Steps:

#### **Morning (5 AM) - Turn Internet ON:**
```
1. Schedule Trigger fires at 5 AM
2. SSH Node: "Check and Create Rule 12"
   - Ensures Rule 12 exists with correct configuration
   - Creates if missing, updates if exists
3. SSH Node: "Enable Internet"
   - Command: set firewall rule 12 disable
   - This DISABLES the DROP rule
   - Traffic is allowed through
4. Telegram: Send "🟢 Internet turned ON" notification
```

#### **Evening (8 PM) - Turn Internet OFF:**
```
1. Schedule Trigger fires at 8 PM
2. SSH Node: "Check and Create Rule 12 (OFF)"
   - Ensures Rule 12 exists with correct configuration
3. SSH Node: "Disable Internet"
   - Command: delete firewall rule 12 disable
   - This ENABLES the DROP rule
   - Traffic is blocked
4. Telegram: Send "🔴 Internet turned OFF" notification
```

---

## 🛠️ Technical Implementation

### SSH Commands Used:

**To Create/Update Rule 12:**
```bash
sg vyattacfg -c "
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper begin && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper set firewall name INTERNET_CONTROL rule 12 action drop && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper set firewall name INTERNET_CONTROL rule 12 source address 192.168.3.0/24 && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper set firewall name INTERNET_CONTROL rule 12 destination address 0.0.0.0/0 && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper set firewall name INTERNET_CONTROL rule 12 description 'Internet control schedule' && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper commit && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper save && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper end
"
```

**To Turn Internet ON (Disable DROP rule):**
```bash
sg vyattacfg -c "
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper begin && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper set firewall name INTERNET_CONTROL rule 12 disable && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper commit && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper save && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper end
"
```

**To Turn Internet OFF (Enable DROP rule):**
```bash
sg vyattacfg -c "
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper begin && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper delete firewall name INTERNET_CONTROL rule 12 disable && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper commit && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper save && 
  /opt/vyatta/sbin/vyatta-cfg-cmd-wrapper end
"
```

### Why `sg vyattacfg -c`?
- VyOS requires special group permissions to modify configuration
- `sg vyattacfg` executes commands with the vyattacfg group
- `vyatta-cfg-cmd-wrapper` provides proper configuration session management

### Command Breakdown:
- `begin` - Start configuration session
- `set/delete` - Modify firewall rules
- `commit` - Apply changes
- `save` - Persist to configuration file
- `end` - Close configuration session

---

## 🔍 Problem-Solving Journey

### Initial Problems Encountered:

1. **"command not found" errors**
   - Issue: Trying to run configure/delete/commit directly
   - Solution: Use vyatta-cfg-cmd-wrapper with proper session management

2. **"set enable" doesn't exist**
   - Issue: VyOS doesn't have an "enable" command
   - Solution: Use "delete disable" to enable rules

3. **Logic confusion**
   - Issue: Mixed up when rule should be active/inactive
   - Solution: 
     - DROP rule DISABLED = Internet ON
     - DROP rule ENABLED = Internet OFF

4. **Rule might not exist**
   - Issue: Workflow fails if Rule 12 doesn't exist
   - Solution: Added "Check and Create" nodes before each action

---

## 📊 Workflow Node Summary

| Node Name | Type | Purpose |
|-----------|------|---------|
| Turn ON at 5 AM | Schedule Trigger | Fires daily at 5:00 AM |
| Turn OFF at 8 PM | Schedule Trigger | Fires daily at 20:00 (8 PM) |
| Check and Create Rule 12 | SSH | Ensures rule exists (ON path) |
| Check and Create Rule 12 (OFF) | SSH | Ensures rule exists (OFF path) |
| Enable Internet | SSH | Disables DROP rule |
| Disable Internet | SSH | Enables DROP rule |
| Send ON Notification | Telegram | Confirms internet enabled |
| Send OFF Notification | Telegram | Confirms internet disabled |

---

## ✅ Features

1. **Automatic Rule Creation** - Creates Rule 12 if missing
2. **Idempotent Operations** - Safe to run multiple times
3. **Status Notifications** - Telegram alerts with execution details
4. **Error Reporting** - Shows stdout/stderr in notifications
5. **Persistent Configuration** - Changes saved to router config
6. **No Manual Intervention** - Fully automated daily schedule

---

## 🎨 User Experience

### Telegram Notifications Include:
- 🟢 or 🔴 emoji for quick visual status
- Execution code (0 = success)
- Standard output from router
- Any error messages
- Timestamp (automatic from Telegram)

---

## 🔐 Security Considerations

1. **SSH Credentials** - Stored securely in n8n credentials manager
2. **Group Permissions** - Uses `sg vyattacfg` for proper authorization
3. **Configuration Commits** - All changes require commit + save
4. **Audit Trail** - Telegram messages provide execution history

---

## 📝 Summary

This solution provides **automated parental controls** or **network scheduling** for the 192.168.3.0/24 subnet. Every day, internet access is:
- **Granted at 5 AM** (15 hours of access)
- **Revoked at 8 PM** (9 hours of no access)

The system is self-maintaining, creates its own firewall rule if needed, and reports status via Telegram. It's a robust, production-ready automation that requires zero daily human intervention.