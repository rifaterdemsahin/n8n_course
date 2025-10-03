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

# 📊 Simple Data Transformation

Using the Set Node

---

## 🎯 Objective

This project demonstrates how to use the **Set node** to create and modify data in an n8n workflow.

---

## 🤖 The Workflow

`set-node-workflow.json`

This simple workflow shows how to:

1.  **Start** the workflow.
2.  Use a **Set node** to create new data fields.
3.  Use a simple **expression** to combine data.
4.  View the final output.

---

## ✨ The Set Node

The `Create & Modify Data` node in the workflow is a **Set node**. Here's what it does:

<div class="columns">
<div>

### Static Values

- Sets `firstName` to "Ada".
- Sets `lastName` to "Lovelace".
- Sets `userID` to `1815`.

</div>
<div>

### Dynamic Expression

- Sets `fullName` using the expression:
  `={{$json.firstName}} {{$json.lastName}}`
- This combines the `firstName` and `lastName` fields.

</div>
</div>

---

## ✅ Key Takeaways

- The **Set node** is essential for data manipulation.
- **Expressions** (using `{{ }}`) allow you to create dynamic data.
- **`$json`** refers to the data of the current item in the workflow.

---

## 📚 External Resources

- **n8n Set Node Documentation**: [https://docs.n8n.io/nodes/n8n-nodes-base.set/](https://docs.n8n.io/nodes/n8n-nodes-base.set/)
- **n8n Expressions Guide**: [https://docs.n8n.io/code-examples/expressions/](https://docs.n8n.io/code-examples/expressions/)