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

# 🌎 Global Variables vs. 🏃 Execution Variables

---

## 🌎 Global Variables

- **Workflow-level** variables that persist across all executions.
- **Scope**: Available to all nodes within the same workflow.
- **Persistence**: Values persist across multiple workflow executions.
- **Access**: `$vars.variableName`
- **Use Cases**: Configuration values, API keys, default settings.

---

## 🏃 Execution Variables

- **Execution-level** variables created during a specific execution.
- **Scope**: Available only within the current execution.
- **Persistence**: Values are lost when the execution completes.
- **Access**: `$vars.variableName`
- **Use Cases**: Temporary data, execution-specific calculations, dynamic values.

---

## 🔑 Key Differences

| Aspect | Global Variables | Execution Variables |
|---|---|---|
| **Scope** | Workflow-wide | Execution-specific |
| **Persistence** | Across executions | Single execution only |
| **Definition** | Set in workflow settings | Set during execution |
| **Use Case** | Configuration, constants | Dynamic, temporary data |

---

## 👍 Best Practices

- **Global Variables**: Use for configuration, constants, and shared data that doesn't change often.
- **Execution Variables**: Use for temporary data, results from nodes, and dynamic values.

---

## ✍️ Syntax and Access

Both types of variables use the same syntax for access:

```javascript
// Access a variable
$vars.myVariable

// Use in expressions
{{ $vars.apiEndpoint }}/users

// Use in code
const value = $vars.tempValue;
```

---

## ⚠️ Common Pitfalls

- Mixing scopes.
- Overusing global variables.
- Variable name conflicts.
- Storing sensitive data in global variables.