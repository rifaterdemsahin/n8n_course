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

# 🧑‍🤝‍🧑 Exploring Community Nodes

Extend n8n's functionality with community-built nodes.

---

## ❓ What are Community Nodes?

Custom nodes built by the n8n community to integrate with services not included in the core n8n package.

<div class="columns">
<div>

### ✅ Benefits

- Access hundreds of new integrations.
- Rapidly connect to new services.
- Get support from an active community.

</div>
<div>

### ⚠️ Considerations

- Review code for security.
- Nodes may not be actively maintained.
- Compatibility is not guaranteed.

</div>
</div>

---

## 🔎 Finding Community Nodes

<div class="columns">
<div>

### n8n Community Hub

- **[n8n.io/integrations](https://n8n.io/integrations/)**
- The official source for community nodes.
- Search, filter, and browse nodes.

</div>
<div>

### GitHub & npm

- Search for `n8n-nodes-*` on GitHub.
- Use `npm search n8n-nodes` to find packages.

</div>
</div>

---

## 💾 Installing Community Nodes

The easiest way to install is with the n8n CLI.

```bash
# Install a community node
n8n install-package n8n-nodes-example

# Install multiple nodes
n8n install-package n8n-nodes-example n8n-nodes-another
```

Remember to restart n8n after installation.

---

## 🤖 The Demo Workflow

`community-node-demo-workflow.json`

This workflow demonstrates a simple use case for a community node.

1.  **Webhook**: Triggers the workflow.
2.  **Set**: Prepares some demo data.
3.  **HTTP Request**: Simulates a call to a community node.
4.  **Set**: Logs the result.

---

## 📚 External Resources

- **n8n Community Hub**: [https://n8n.io/integrations/](https://n8n.io/integrations/)
- **n8n Documentation on Community Nodes**: [https://docs.n8n.io/integrations/community-nodes/](https://docs.n8n.io/integrations/community-nodes/)
- **Create your own node**: [https://docs.n8n.io/integrations/creating-nodes/](https://docs.n8n.io/integrations/creating-nodes/)