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

# 💾 Backup and Version Your Workflows

Protecting your automation investment.

---

## 🤔 Why is this important?

- **Disaster Recovery**: Restore workflows after a failure.
- **Change Tracking**: See who changed what, and when.
- **Collaboration**: Safely work on workflows with a team.
- **Rollbacks**: Easily revert to a previous working version.

---

## 🛠️ Backup & Versioning Methods

<div class="columns">
<div>

### n8n Built-in Versioning

- Access workflow **History** tab.
- Restore previous versions with one click.

</div>
<div>

### Manual Backups

- Export workflows as JSON files.
- Store them in a safe place (like cloud storage).

</div>
</div>

<div class="columns">
<div>

### Git-based Version Control

- The **best** way to manage workflows.
- Use a Git repository (like GitHub) to store your workflow files.

</div>
<div>

### Automated Backups

- Create a workflow that automatically backs up other workflows.
- Schedule it to run daily or weekly.

</div>
</div>

---

## 🤖 The Demo Workflow

`backup-versioning-demo-workflow.json`

This workflow shows how you can automate backups:

1.  **Cron Trigger**: Runs on a schedule.
2.  **Set**: Prepares backup metadata.
3.  **HTTP Request**: Exports workflow data (simulated).
4.  **HTTP Request**: Uploads the backup to a server (simulated).
5.  **Slack**: Sends a notification that the backup was successful.

---

## ✅ Best Practices

- **Use Git** for version control.
- **Automate your backups**.
- **Store backups in a separate location** (e.g., cloud storage).
- **Test your recovery process** regularly.
- **Don't store credentials** in your workflow files.

---

## 📚 External Resources

- **n8n Documentation on Version Control**: [https://docs.n8n.io/editor/version-control/](https://docs.n8n.io/editor/version-control/)
- **Git Handbook**: [https://guides.github.com/introduction/git-handbook/](https://guides.github.com/introduction/git-handbook/)