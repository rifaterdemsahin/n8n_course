---
marp: true
theme: default
---

# The IF Node - Adding Logic to Your Workflows

---

## Understanding the IF Node

- **What is the IF Node?**
  - A conditional node that creates different execution paths based on specified conditions.
- **How it Works**
  - Evaluates data and routes the workflow down true/false branches.
- **Key Features**
  - Binary Decision Making
  - Multiple Condition Types
  - Flexible Logic (AND/OR)
  - Data Preservation

---

## Basic IF Node Configuration

- **Simple Condition Setup**
  - Add IF Node, configure conditions, test, and connect outputs.
- **Condition Structure**
  - Defined with `leftValue`, `operator`, and `rightValue`.
- **Workflow Structure**
  - Trigger -> Data -> IF Node -> True/False Branches -> Merge -> Output

---

## Condition Types and Operators

- **String Conditions**
  - `equals`, `contains`, `startsWith`, `regex`, etc.
- **Number Conditions**
  - `equals`, `gt`, `lt`, `between`, etc.
- **Boolean Conditions**
  - `equal`, `notEqual`.
- **Date Conditions**
  - `equals`, `before`, `after`, `between`.

---

## Advanced Condition Logic

- **Multiple Conditions**
  - **AND Logic**: All conditions must be true.
  - **OR Logic**: Any condition can be true.
- **Complex Condition Examples**
  - E-commerce order processing, weather alerts.
- **Expression-Based Conditions**
  - Use JavaScript expressions for complex calculations.

---

## Practical Examples

- **Basic Temperature Alert**
- **E-commerce Order Processing**
- **User Authentication Flow**
- **Content Moderation System**

---

## Best Practices

- **Condition Design**: Clear, readable, and consistent data types.
- **Performance Optimization**: Efficient condition ordering, avoid complex expressions.
- **Error Handling**: Safe data access and validation before conditions.
- **Documentation and Naming**: Descriptive node names and comments.

---

## Common Use Cases

- **Data Filtering**
- **Business Logic**
- **Error Handling**
- **Routing and Workflow Control**

---

## Conclusion

- The IF node is fundamental for creating intelligent, decision-making workflows.
- Master its capabilities to build dynamic, robust, and efficient automations.