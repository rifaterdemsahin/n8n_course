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

# 📢 Project - Automated Discord/Slack Notifications

---

## 📝 Project Overview

- 🎓 Learn how to create automated notification workflows for Discord and Slack using n8n.
- 🔗 Connect your accounts, create workflows, send custom messages, and handle errors.

---

## 🎯 Learning Objectives

- 🔗 Connect Discord/Slack accounts to n8n.
- 👆 Create manual trigger workflows.
- 🔀 Implement conditional logic for message types.
- 🎨 Format rich messages with embeds and attachments.
- gracefully Handle errors gracefully.

---

## 💬 Part 1: Discord Notifications

- **Setup**: Create a Discord webhook and configure it in n8n.
- **Workflow Features**:
  - Manual Trigger
  - Default Values Setup
  - Conditional Message Formatting
  - Rich Discord Embeds
  - Response Formatting

---

## slack Part 2: Slack Notifications

- **Setup**: Create a Slack App, configure bot permissions, and set up credentials in n8n.
- **Workflow Features**:
  - Manual Trigger
  - Default Configuration
  - Message Type Handling
  - Rich Slack Attachments
  - Error Handling

---

## 🚀 Advanced Features

- динамический **Dynamic Content**: Use n8n expressions to create dynamic messages.
- 📝 **Message Templates**: Create reusable message templates for Discord and Slack.
- 🚨 **Error Handling**: Implement try-catch logic and fallback notifications.

---

## 🛠️ Troubleshooting

- **Discord**: "Invalid Webhook", "Message Not Appearing".
- **Slack**: "Invalid Auth Token", "Channel Not Found", "Missing Scope".
- **General**: Test credentials, check workflow execution, verify node configuration.

---

## 🔒 Security Best Practices

- 🔑 **Credential Management**: Never share webhook URLs or OAuth tokens.
- 🛡️ **Channel Security**: Use private channels for sensitive information.
- ✉️ **Message Content**: Sanitize user input and avoid sending sensitive data.

---

## ✅ Conclusion

- You have learned how to build automated notification workflows for Discord and Slack.
- You can now connect to other services, create more sophisticated logic, and customize notifications.
