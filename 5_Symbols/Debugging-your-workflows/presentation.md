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

# 🐛 Debugging Your Workflows

---

## 🤔 Key Debugging Concepts

- **Execution Flow**: Understand how data moves through your workflow.
- **Data Inspection**: Examine input, output, and error data.
- **Execution Logs**: Review detailed logs of what happened.

---

## 🛠️ Common Debugging Techniques

- **Using the Set Node**: Inspect data, add debug info, and create test data.
- **Using the Do Nothing Node**: Break execution flow, test specific parts, and create manual checkpoints.

---

## 🧩 Debugging Workflow Patterns

- **Data Inspection**: `Start → Set (debug) → Logic → Set (inspect) → End`
- **Conditional Debugging**: `Start → IF → Do Nothing (debug) → Continue`
- **Error Handling**: `Start → Try → Catch → Set (log error) → Handle`

---

## 👍 Best Practices

- Use descriptive names for debugging nodes.
- Add timestamps to track execution timing.
- Log important variables at key points.
- Use the Do Nothing node for intentional stopping points.
- Test with small datasets first.

---

## 🧰 Debugging Tools in n8n

- **Execution History**: View past executions.
- **Node Data Viewer**: Inspect input/output data.
- **Execution Logs**: Detailed logs of what happened.
- **Error Messages**: Clear error descriptions.
- **Data Preview**: See data structure before processing.

---

## 常見問題與解決方案

- **Data Not Flowing**: Check connections and data structure.
- **Unexpected Results**: Inspect intermediate results with Set nodes.
- **Performance Issues**: Isolate bottlenecks with Do Nothing nodes.