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

# 🐛 Debugging Your Workflows

See what happens behind the scenes.

---

## 🔍 Key Debugging Concepts

<div class="columns">
<div>

### ➡️ Execution Flow

- Workflows run sequentially.
- Data flows from one node to the next.

</div>
<div>

### 🕵️ Data Inspection

- Check **input** and **output** data for each node.
- Use the **Execution Logs** to see what happened.

</div>
</div>

---

## 🛠️ Debugging Tools

Two of the most useful nodes for debugging are **Set** and **Do Nothing**.

<div class="columns">
<div>

### The Set Node

- **Inspect data** at any point.
- **Add debug info** like timestamps.
- **Create test data**.

</div>
<div>

### The Do Nothing Node

- **Pause** execution.
- **Isolate** parts of your workflow.
- Create manual **checkpoints**.

</div>
</div>

---

## 🤖 Example Workflows

This lesson includes two example workflows:

- **`set-and-edit-node-workflow.json`**: Shows how to use the **Set** node to add and inspect debugging information.

- **`do-nothing-node-workflow.json`**: Demonstrates using the **Do Nothing** node to create checkpoints and pause execution.

---

## ✅ Best Practices

- Use **descriptive names** for debug nodes.
- Add **timestamps** to track timing.
- Log important **variables**.
- Test with **small datasets** first.

---

## 📚 External Resources

- **n8n Debugging Documentation**: [https://docs.n8n.io/getting-started/debugging/](https://docs.n8n.io/getting-started/debugging/)
- **n8n Community Forum (Debugging)**: [https://community.n8n.io/c/question/debugging/11](https://community.n8n.io/c/question/debugging/11)