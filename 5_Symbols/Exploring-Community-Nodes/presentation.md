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

# 🌐 Exploring Community Nodes

---

## 🤔 What are Community Nodes?

- Custom-built nodes created by the n8n community.
- Extend n8n's functionality beyond the core nodes.
- Integrate with third-party APIs, specialized services, and custom business logic.

---

## 🔍 Finding Community Nodes

- **n8n Community Hub**: The official source for community nodes.
- **GitHub Repository**: Search for `n8n-nodes-*` repositories.
- **Community Forums**: Discover new nodes and get help.
- **Package Managers**: Search for `n8n-nodes` on npm.

---

## 📥 Installing Community Nodes

- **Using n8n CLI**: `n8n install-package n8n-nodes-example`
- **Manual Installation**: Clone from Git and build manually.
- **Docker Installation**: Add installation commands to your Dockerfile.

---

## 🌟 Popular Community Nodes

- **Database**: PostgreSQL, MySQL, MongoDB.
- **API Integration**: Stripe, Twilio, Salesforce.
- **File Processing**: PDF, Excel.
- **Communication**: Telegram, WhatsApp.
- **Utility**: Crypto, Date/Time.

---

## 👨‍💻 Creating Your Own Community Nodes

- **Node Structure**: Follow the n8n node structure and implement the `INodeType` interface.
- **Development Setup**: Set up a TypeScript project for your node.
- **Testing**: Write unit tests for your node.
- **Publishing**: Publish your node to npm.

---

## 👍 Best Practices

- **Security**: Review code before installation and use minimal permissions.
- **Maintenance**: Keep nodes updated and test updates in a development environment.
- **Documentation**: Provide clear installation instructions and usage examples.
- **Performance**: Optimize API calls and manage resources efficiently.

---

## 🛠️ Troubleshooting

- **Installation Failures**: Check n8n version compatibility and clear npm cache.
- **Node Not Appearing**: Restart n8n and check logs for errors.
- **Credential Issues**: Verify credential format and API key permissions.
- **Performance Issues**: Monitor resource usage and implement rate limiting.

---

## ✅ Conclusion

- Community nodes significantly extend n8n's capabilities.
- Follow best practices for finding, installing, and maintaining community nodes.
- Contribute back to the community by creating and sharing your own nodes.