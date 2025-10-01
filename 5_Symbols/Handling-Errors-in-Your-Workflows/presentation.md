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

# 🚨 Handling Errors in Your Workflows

---

## 🤔 Understanding Error Types

- **API Errors**: Rate Limiting, Authentication, Network Issues, Service Unavailable.
- **Data Errors**: Invalid Format, Missing Fields, Type Mismatches, Validation Failures.
- **Configuration Errors**: Missing Credentials, Invalid Settings, Permission Issues, Resource Limits.
- **Logic Errors**: Conditional Logic, Expression Errors, Loop Issues, Data Flow.

---

## 介紹錯誤工作流程

- **What are Error Workflows?**
  - Specialized workflows that automatically execute when your main workflow encounters an error.
- **Setting Up Error Workflows**
  - Create an error workflow with an "Error Trigger".
  - Link it to your main workflow in the settings.

---

## 📊 Monitoring Executions

- **Accessing Execution Logs**: View execution history in the n8n interface.
- **Execution Status Indicators**: Success (🟢), Error (🔴), Running (🟡), Waiting (⏸️).
- **Failed Run Analysis**: Identify failure patterns and debug issues.

---

## 🧩 Error Handling Design Patterns

- **Try-Catch Pattern**: Handle errors within the workflow.
- **Circuit Breaker Pattern**: Prevent cascading failures.
- **Retry with Exponential Backoff**: Automatically retry failed operations with increasing delays.
- **Graceful Degradation**: Provide a fallback or degraded service.

---

## 🐛 Debugging Techniques

- **Node-Level Debugging**: Use "No Operation" and "Set" nodes to inspect data.
- **Expression Debugging**: Use safe access and test expressions in "Set" nodes.
- **Data Flow Tracing**: Add trace IDs to track data through the workflow.

---

## 👍 Best Practices

- **Preventive Measures**: Validate inputs and configurations.
- **Error Recovery Strategies**: Use automatic retries and fallback operations.
- **Monitoring and Alerting**: Monitor error rates and performance.

---

## 🌐 Real-World Examples

- **Email Processing with Error Handling**
- **API Integration with Circuit Breaker**
- **Data Validation Pipeline**

---

## ✅ Conclusion

- Effective error handling is crucial for building reliable n8n workflows.
- Implement a combination of error workflows, monitoring, and design patterns.
- Test error scenarios and document your error handling procedures.