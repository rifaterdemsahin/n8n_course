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

# 🛡️ Handling Errors in Your Workflows

Building robust and resilient automation.

---

## 🤔 Understanding Error Types

Errors can come from many places.

<div class="columns">
<div>

### API Errors

- Rate Limiting
- Authentication Issues
- Network Problems

</div>
<div>

### Data & Logic Errors

- Invalid Format
- Missing Fields
- Incorrect `IF` conditions

</div>
</div>

---

## 🚨 Error Workflows

An **Error Workflow** is a special workflow that runs automatically when another workflow fails.

- **Centralized** error handling.
- **Triggered** by an **Error Trigger** node.
- Can be used to send notifications, retry tasks, or log errors.

---

## 🤖 The Demo Workflow

`error-handling-demo-workflow.json`

This workflow shows a simple error handling pattern:

1.  **Webhook**: Starts the workflow.
2.  **HTTP Request**: Tries to make an API call. This node has an **Error Workflow** attached.
3.  **On Success**: A `Set` node logs a success message.
4.  **On Failure**: The error workflow is triggered, which sends a Slack notification.

---

## ✅ Best Practices

- **Use Error Workflows** for critical processes.
- **Validate input data** to prevent errors.
- Use **`try/catch` blocks** in Code nodes.
- **Monitor executions** to spot recurring issues.

---

## 📚 External Resources

- **n8n Error Handling Documentation**: [https://docs.n8n.io/error-handling/](https://docs.n8n.io/error-handling/)
- **Error Workflow Tutorial**: [https://n8n.io/blog/error-workflow/](https://n8n.io/blog/error-workflow/)