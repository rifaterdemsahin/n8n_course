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

# 🛠️ Environment Setup & Configuration

Setting up your n8n environment for success.

---

## 🌍 Setup Options

You have two main choices for your n8n environment.

<div class="columns">
<div>

### ☁️ n8n Cloud

- **Pros**: Easy setup, no server management.
- **Cons**: Subscription cost, less customization.
- **Best For**: Beginners, small projects.

</div>
<div>

### 🖥️ Self-Hosted

- **Pros**: Full control, cost-effective at scale.
- **Cons**: Requires server management.
- **Best For**: Production, advanced users.

</div>
</div>

---

## ✅ Setup Checklist

A high-level look at what you need to do.

<div class="columns">
<div>

### n8n Cloud

1.  Create an account.
2.  Verify your email.
3.  Complete the workspace setup.
4.  Start building!

</div>
<div>

### Self-Hosted (Docker)

1.  Install Docker.
2.  Configure n8n.
3.  Set up storage.
4.  (Optional) Configure reverse proxy & SSL.

</div>
</div>

---

## ⚙️ Key Configuration Topics

- **Environment Variables**: For database, auth, and security settings.
- **Security**: Manage users, API keys, and credential encryption.
- **Performance**: Optimize resources, caching, and load balancing.

---

## 📚 External Resources

- **n8n Documentation**: [https://docs.n8n.io/](https://docs.n8n.io/)
- **n8n Community Forum**: [https://community.n8n.io/](https://community.n8n.io/)
- **Docker Installation**: [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/)