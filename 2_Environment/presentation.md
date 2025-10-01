---
marp: true
theme: default
style: |
  section {
    background-color: #1a1a2e;
    color: #eee;
  }
  h1, h2 {
    color: #ff6b35;
  }
  h3 {
    color: #4a90e2;
  }
  a {
    color: #4a90e2;
  }
  code {
    background-color: #16213e;
    color: #ff6b35;
  }
  strong {
    color: #ff6b35;
  }
  ul {
    padding-right: 200px;
  }
  section::after {
    content: '';
    position: absolute;
    bottom: 0;
    right: 0;
    width: 180px;
    height: 180px;
  }
paginate: true
---

# 🚀 Setting Up Your n8n Environment

## From Zero to Workflow Automation ⚙️

---

# What is n8n? 🤖

**n8n** is a free and source-available workflow automation tool.

* 🔗 **Connect APIs** - Link to any app or service
* 🧠 **Visual Workflow Editor** - No coding required!
* 🏠 **Self-hostable** - Full control over your data
* 🧑‍💻 **Extendable** - Custom nodes with JS/TS

---

# Why Different Environments? 🌳

Running everything in one place is risky! Standard setup:

* **🛠️ Development** - Your local machine for building & testing

* **🧪 Staging** - Production clone for final testing

* **🌍 Production** - Live environment for business-critical workflows
  **Handle with care!**

---

# Prerequisites 📋

Before starting with Docker setup, you need:

* **🐳 Docker** - Core technology for isolated containers
  [Get Docker](https://docs.docker.com/get-docker/)

* **↔️ Docker Compose** - Multi-container management
  (Included with Docker Desktop)

* **✔️ git** - Clone configuration repository

---

# The Core: docker-compose.yml 🏗️

The blueprint for your n8n service:

* **n8n service** - Main application container
* **Database service** - PostgreSQL for persistence
* **Volumes** - Data survives container restarts

```yaml
services:
  n8n:
    image: n8nio/n8n
  database:
    image: postgres:14
```

---

# Configuration: The .env File 🔑

**Never put secrets in docker-compose.yml!**

Use `.env` for environment variables:
* Database credentials
* Timezone settings
* Encryption key (critical!)

```ini
POSTGRES_DB=n8n
POSTGRES_USER=n8nuser
POSTGRES_PASSWORD=mysecretpassword
N8N_ENCRYPTION_KEY=averylongandrandomstring
GENERIC_TIMEZONE=Europe/London
```

---

# Docker Setup: Let's Go! 🛠️

**Step-by-step installation:**

1. **Clone repository**
   ```bash
   git clone https://github.com/n8n-io/n8n-docker-compose.git
   cd n8n-docker-compose
   ```

2. **Create environment file**
   ```bash
   cp .env.example .env
   ```

---

# Docker Setup: Let's Go! 🛠️

**Step-by-step installation:**

3. **Edit `.env` file**
   Set custom values, especially `N8N_ENCRYPTION_KEY`

4. **Launch! 🚀**
   ```bash
   docker-compose up -d
   ```

---

# Is it Working? ✅

Containers are running in the background!

* Open your web browser
* Navigate to: **http://localhost:5678**
* Create your owner account

**Success!** 🎉

---

# Managing Your Instance 🕹️

Essential Docker Compose commands:

* **Stop containers**
  `docker-compose stop`

* **Start containers**
  `docker-compose start`

* **View logs**
  `docker-compose logs -f n8n`

* **Remove containers**
  `docker-compose down`

---

# Beyond Docker: Other Options 🗺️

Docker Compose is great, but alternatives exist:

1. **☁️ Managed Cloud (Easy)** - Railway
2. **⚙️ Advanced Self-Hosted (Hard)** - Proxmox LXC

Let's explore both!

---

# Cloud Option: Railway.app 🚂

Modern PaaS for simple deployment

**✅ Pros:**
* One-click deployment
* No server management
* Automatic SSL & custom domains
* Auto-scaling with database

**❌ Cons:**
* More expensive than self-hosting
* Less server control

**Best for:** Quick start without infrastructure hassle

---

# Advanced: Proxmox LXC 🐧

For home lab enthusiasts with Proxmox VE

**High-level steps:**
1. Create LXC Container (Debian/Ubuntu)
2. Install Node.js and npm
3. Install n8n: `npm install n8n -g`
4. Use pm2 process manager
5. Setup reverse proxy for SSL

**Best for:** Advanced Linux users

---

# Questions? 🤔

---

# 📚 Further Reading & Resources

**Official Documentation & Links:**

* [n8n Official Documentation](https://docs.n8n.io/)
* [n8n Docker Compose Setup Guide](https://docs.n8n.io/hosting/installation/docker-compose/)
* [Deploy n8n on Railway](https://railway.app/template/n8n)
* [n8n Community Forum](https://community.n8n.io/)

**Happy Automating!** 🚀⚙️