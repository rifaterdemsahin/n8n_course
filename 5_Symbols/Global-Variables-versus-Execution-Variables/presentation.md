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

# 🌎 Global vs. Execution Variables

Understanding variable scope in n8n.

---

## ✌️ Two Types of Variables

<div class="columns">
<div>

### 🌍 Global Variables

- **Scope**: Workflow-wide.
- **Persistence**: Across all executions.
- **Use Case**: Configuration, API keys, constants.

</div>
<div>

### 🏃 Execution Variables

- **Scope**: Single execution only.
- **Persistence**: Lost after execution.
- **Use Case**: Temporary data, dynamic values.

</div>
</div>

---

## 🔑 Key Differences

| Aspect      | Global Variables        | Execution Variables     |
|-------------|-------------------------|-------------------------|
| **Scope**   | Workflow-wide           | Execution-specific      |
| **Persistence** | Across executions       | Single execution only   |
| **Use Case**  | Configuration, constants| Dynamic, temporary data |

---

## 🤖 Example Workflows

This lesson includes two example workflows:

- **`global-variables-workflow.json`**: Shows how to define and use **global variables** for things like API endpoints and keys.

- **`execution-variables-workflow.json`**: Demonstrates how to use **execution variables** to store temporary data during a single workflow run.

---

## ✅ Best Practices

- Use **descriptive names** for your variables.
- Use **global variables** for static data that doesn't change often.
- Use **execution variables** for dynamic data that is specific to one run.
- Don't store sensitive data in variables if you can use credentials.

---

## 📚 External Resources

- **n8n Documentation on Variables**: [https://docs.n8n.io/core-concepts/variables/](https://docs.n8n.io/core-concepts/variables/)