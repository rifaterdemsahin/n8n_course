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

# 📎 Sending Multiple Attachments

How to send multiple files in a single email.

---

## 🎯 Objective

This project demonstrates how to fetch multiple files from different sources and send them as attachments in a single email using n8n.

---

## 🤖 The Workflow

`multi-attachment-workflow.json`

1.  **Manual Trigger**: Starts the workflow.
2.  **GitHub Nodes (x4)**: Fetches four different files from a GitHub repository.
3.  **Merge Node**: Combines the four files into a single stream.
4.  **Aggregate Node**: Gathers all the binary data from the files.
5.  **Gmail Node**: Sends an email with the four files as attachments.

---

## ✨ Key Nodes

<div class="columns">
<div>

### Merge Node

- Combines multiple incoming data streams into one.
- Essential for gathering files from different sources.

</div>
<div>

### Aggregate Node

- Collects all binary data from the merged files.
- **Crucial**: You must enable the `Include Binaries` option.

</div>
</div>

---

## ✅ How it Works

- The workflow runs four `GitHub` nodes in parallel to download the files faster.
- The `Merge` node waits for all four files to be downloaded.
- The `Aggregate` node creates a single item with all the file data.
- The `Gmail` node is configured to use the binary data from the `Aggregate` node as attachments.

---

## 📚 External Resources

- **n8n Merge Node Documentation**: [https://docs.n8n.io/nodes/n8n-nodes-base.merge/](https://docs.n8n.io/nodes/n8n-nodes-base.merge/)
- **n8n Aggregate Node Documentation**: [https://docs.n8n.io/nodes/n8n-nodes-base.aggregate/](https://docs.n8n.io/nodes/n8n-nodes-base.aggregate/)