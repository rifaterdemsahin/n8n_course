---
marp: true
theme: uncover
style: |
  .columns {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1rem;
  }
  h1, h2, h3, h4, h5, h6 {
    color: #0277b5;
  }
  a {
    color: #f89d21;
  }
  strong {
    color: #f89d21;
  }
  
---

#  automating your life with n8n

---

## 🎯 Objective

**Automate network internet access** for `192.168.3.0/24` using a VyOS/EdgeOS firewall.

- **Schedule**: Turn internet ON and OFF at specific times.
- **Tools**: n8n, SSH, and Telegram for notifications.
- **Result**: A fully automated, hands-free system.

---

## 🔧 How It Works: The Logic

The core of the system is a firewall **DROP rule (Rule 12)**.

<div class="columns">
<div>

### 🌞 Internet ON ✅

- **Action**: The DROP rule is **DISABLED**.
- **Result**: Traffic flows freely.
- **Command**: `set firewall rule 12 disable`

</div>
<div>

### 🌚 Internet OFF ❌

- **Action**: The DROP rule is **ENABLED**.
- **Result**: Traffic is blocked.
- **Command**: `delete firewall rule 12 disable`

</div>
</div>

---

## 🔄 The n8n Workflow

This workflow runs on a daily schedule to control the firewall.

<div class="columns">
<div>

### 🌅 5:00 AM - Internet ON

1.  **Trigger**: `ScheduleTrigger` fires.
2.  **SSH**: Ensures **Rule 12** exists.
3.  **SSH**: **Disables** the DROP rule.
4.  **Telegram**: Sends "🟢 Internet ON" notification.

</div>
<div>

### 🌃 8:00 PM - Internet OFF

1.  **Trigger**: `ScheduleTrigger` fires.
2.  **SSH**: Ensures **Rule 12** exists.
3.  **SSH**: **Enables** the DROP rule.
4.  **Telegram**: Sends "🔴 Internet OFF" notification.

</div>
</div>

---

## 🤖 n8n Workflow Explained

Here is a breakdown of the nodes in the `turn-on-off-internet.json` file.

- **ScheduleTrigger (x2)**: One for 5 AM, one for 8 PM.
- **SSH (x4)**:
    - Two to check and create the firewall rule (idempotent).
    - One to disable the rule (Internet ON).
    - One to enable the rule (Internet OFF).
- **Telegram (x2)**: Sends success notifications for both ON and OFF actions.

---

## 🔍 Technical Deep Dive

- **`vyatta-cfg-cmd-wrapper`**: The key to modifying the VyOS configuration. It ensures commands are run with the correct permissions and within a proper session.
- **Idempotency**: The "Check and Create" nodes make the workflow robust. It doesn't fail if the rule already exists.
- **Secure Credentials**: SSH and Telegram credentials are not stored in the workflow JSON. They are managed by n8n's credential manager.

---

## 📚 External Resources

- **n8n Documentation**: [https://docs.n8n.io/](https://docs.n8n.io/)
- **VyOS Documentation**: [https://docs.vyos.io/](https://docs.vyos.io/)
- **Marpit Markdown Presentations**: [https://marpit.marp.app/](https://marpit.marp.app/)