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

# 🤝 The Merge Node

Combining data from different sources.

---

## 🎯 What is the Merge Node?

The **Merge node** combines data from multiple incoming branches into a single output. It's perfect for when you have parallel workflows and need to bring the data back together.

---

## ⚙️ Merge Modes

The Merge node has several modes to combine data:

<div class="columns">
<div>

### Append

- Adds the items from the second input to the end of the first input.

</div>
<div>

### Merge by Index

- Combines items based on their position (e.g., first item with first item).

</div>
</div>

<div class="columns">
<div>

### Merge by Key

- Combines items that have the same value in a specific field (like a user ID).

</div>
<div>

### Merge by Position

- Combines items based on which input they came from.

</div>
</div>

---

## 🤖 The Demo Workflow

`merge-data-workflow.json`

This workflow demonstrates how to merge customer data with order data:

1.  **Get Customer Data**: Fetches a list of customers.
2.  **Get Order Data**: Fetches a list of orders.
3.  **Merge Node**: Combines the two lists using the `customerId` as the key.
4.  **Set Node**: Adds some metadata to the merged data.
5.  **HTTP Request**: Sends the merged data to another service.

---

## ✅ Best Practices

- **Choose the right merge mode** for your use case.
- **Ensure your key fields are consistent** when using "Merge by Key".
- **Validate your data** before and after merging to ensure data quality.

---

## 📚 External Resources

- **n8n Merge Node Documentation**: [https://docs.n8n.io/nodes/n8n-nodes-base.merge/](https://docs.n8n.io/nodes/n8n-nodes-base.merge/)