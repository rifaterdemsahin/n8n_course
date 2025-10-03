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

# 💬 Automated Discord & Slack Notifications

Keep your team in the loop.

---

## 🎯 Project Overview

This project demonstrates how to send automated notifications to **Discord** and **Slack** using n8n.

<div class="columns">
<div>

### 🤖 Discord

- Use **webhooks** to send messages.
- Format messages with **embeds**.

</div>
<div>

### 🤖 Slack

- Use the **Slack API** to send messages.
- Format messages with **attachments**.

</div>
</div>

---

##  workflows

This project includes two workflows:

- **`discord-notifications-workflow.json`**: Sends a message to a Discord channel with a colored embed based on the message type (info or error).

- **`slack-notifications-workflow.json`**: Sends a message to a Slack channel with a colored attachment based on the message type.

---

## ✨ Features

- **Conditional Formatting**: Message color and icon change based on whether the message is a success or an error.
- **Rich Messages**: Uses embeds (Discord) and attachments (Slack) to create visually appealing notifications.
- **Dynamic Content**: Uses n8n expressions to include timestamps and other dynamic data.

---

## ✅ Best Practices

- Use **n8n credentials** to securely store your webhook URLs and API tokens.
- Use an **`IF` node** to handle different message types.
- Use a **`Set` node** to build your message content before sending.

---

## 📚 External Resources

- **Discord Webhook Documentation**: [https://discord.com/developers/docs/resources/webhook](https://discord.com/developers/docs/resources/webhook)
- **Slack API Documentation**: [https://api.slack.com/](https://api.slack.com/)