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

# 🤔 The IF Node

Adding conditional logic to your workflows.

---

## 🎯 What is the IF Node?

The **IF node** lets you create different paths in your workflow based on conditions. It's like asking a "yes" or "no" question about your data.

<div class="columns">
<div>

### ✅ True Path

- If the condition is met, the workflow continues down the "true" path.

</div>
<div>

### ❌ False Path

- If the condition is not met, it goes down the "false" path.

</div>
</div>

---

## 🤖 The Demo Workflows

This lesson includes two example workflows:

- **`basic-if-node-workflow.json`**: A simple workflow that checks if the temperature is above 30°C and sends a different message for hot or normal weather.

- **`multiple-conditions-workflow.json`**: A more complex example that uses multiple `IF` nodes to check for different discount conditions for an e-commerce order.

---

## ✨ Condition Types

You can create conditions for different data types:

- **String**: `equals`, `contains`, `starts with`, `regex`, etc.
- **Number**: `equals`, `greater than`, `less than`, `between`, etc.
- **Boolean**: `true` or `false`.
- **Date**: `before`, `after`, `between`, etc.

---

## 🤝 Combining Conditions

You can use multiple conditions in a single `IF` node.

<div class="columns">
<div>

### AND

- **All** conditions must be true.

</div>
<div>

### OR

- **Any** of the conditions can be true.

</div>
</div>

---

## 📚 External Resources

- **n8n IF Node Documentation**: [https://docs.n8n.io/nodes/n8n-nodes-base.if/](https://docs.n8n.io/nodes/n8n-nodes-base.if/)