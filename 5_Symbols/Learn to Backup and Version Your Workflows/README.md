# Learn to Backup and Version Your Workflows

## Overview

This guide covers essential practices for backing up and versioning your n8n workflows. Proper version control and backup strategies are crucial for maintaining reliable automation systems in production environments.

## Table of Contents

1. [Why Workflow Backup and Versioning Matters](#why-workflow-backup-and-versioning-matters)
2. [Built-in n8n Versioning](#built-in-n8n-versioning)
3. [Manual Backup Strategies](#manual-backup-strategies)
4. [Git-based Version Control](#git-based-version-control)
5. [Automated Backup Solutions](#automated-backup-solutions)
6. [Best Practices](#best-practices)
7. [Recovery Procedures](#recovery-procedures)

## Why Workflow Backup and Versioning Matters

### Common Scenarios Requiring Backup/Versioning:

- **Workflow Corruption**: Unexpected data loss or corruption
- **Accidental Changes**: Modifications that break existing functionality
- **Environment Migration**: Moving workflows between development, staging, and production
- **Team Collaboration**: Multiple developers working on the same workflows
- **Rollback Needs**: Reverting to a previous working version
- **Audit Requirements**: Tracking changes for compliance purposes

### Benefits of Proper Versioning:

- **Disaster Recovery**: Quick restoration after failures
- **Change Tracking**: Understanding what changed and when
- **Collaboration**: Safe multi-developer workflows
- **Testing**: Ability to test changes without affecting production
- **Documentation**: Automatic documentation of workflow evolution

## Built-in n8n Versioning

### Workflow History

n8n provides built-in workflow versioning:

1. **Access Workflow History**:
   - Open any workflow
   - Click the "History" tab
   - View all saved versions

2. **Version Information**:
   - Version number
   - Last modified date
   - User who made changes
   - Change summary

3. **Restore Previous Versions**:
   - Select desired version
   - Click "Restore"
   - Confirm restoration

### Automatic Versioning Settings

Configure automatic versioning in n8n settings:

```javascript
// n8n Configuration
{
  "workflows": {
    "autoSave": true,
    "saveManualExecutions": true,
    "versionControl": {
      "enabled": true,
      "maxVersions": 50,
      "autoVersion": true
    }
  }
}
```

## Manual Backup Strategies

### 1. Export Individual Workflows

#### Export Process:
1. **Open Workflow**: Navigate to the workflow you want to backup
2. **Export**: Click the "Export" button (three dots menu)
3. **Choose Format**: Select JSON format
4. **Save File**: Download the workflow file
5. **Organize**: Store in organized folder structure

#### File Naming Convention:
```
workflows/
├── production/
│   ├── email-automation-v1.2.3.json
│   ├── data-sync-v2.1.0.json
│   └── notifications-v1.0.0.json
├── staging/
│   └── email-automation-v1.2.4-beta.json
└── development/
    └── experimental-features-v0.1.0.json
```

### 2. Bulk Export All Workflows

#### Using n8n CLI:
```bash
# Export all workflows
n8n export:workflow --output=./backups/workflows-$(date +%Y%m%d).json

# Export specific workflows
n8n export:workflow --ids="1,2,3" --output=./backups/selected-workflows.json
```

#### Using API:
```bash
# Get all workflow IDs
curl -X GET "http://localhost:5678/api/v1/workflows" \
  -H "Authorization: Bearer YOUR_API_TOKEN"

# Export specific workflow
curl -X GET "http://localhost:5678/api/v1/workflows/1" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -o workflow-1.json
```

### 3. Database Backup

#### Complete n8n Instance Backup:
```bash
# PostgreSQL backup
pg_dump n8n_db > n8n_backup_$(date +%Y%m%d_%H%M%S).sql

# SQLite backup
cp n8n.db n8n_backup_$(date +%Y%m%d_%H%M%S).db
```

## Git-based Version Control

### 1. Initialize Git Repository

```bash
# Create project directory
mkdir n8n-workflows
cd n8n-workflows

# Initialize Git repository
git init

# Create .gitignore
cat > .gitignore << EOF
# Sensitive data
*.env
*.key
*.pem

# Temporary files
*.tmp
*.log

# Node modules (if using custom nodes)
node_modules/

# OS files
.DS_Store
Thumbs.db
EOF
```

### 2. Workflow Organization Structure

```
n8n-workflows/
├── .git/
├── .gitignore
├── README.md
├── workflows/
│   ├── production/
│   │   ├── email-automation.json
│   │   ├── data-sync.json
│   │   └── notifications.json
│   ├── staging/
│   │   └── email-automation-staging.json
│   └── development/
│       └── experimental.json
├── credentials/
│   ├── production.json.example
│   └── staging.json.example
├── scripts/
│   ├── backup.sh
│   ├── deploy.sh
│   └── restore.sh
└── docs/
    ├── deployment-guide.md
    └── workflow-documentation.md
```

### 3. Git Workflow for n8n

#### Development Branch Strategy:
```bash
# Main branches
git checkout -b main
git checkout -b develop

# Feature branches
git checkout -b feature/new-email-workflow
git checkout -b bugfix/fix-data-sync
git checkout -b hotfix/critical-security-fix
```

#### Commit Messages Convention:
```bash
# Format: type(scope): description
git commit -m "feat(email): add attachment processing to email workflow"
git commit -m "fix(sync): resolve duplicate data issue in sync workflow"
git commit -m "docs(readme): update deployment instructions"
git commit -m "refactor(notifications): simplify notification logic"
```

### 4. Automated Git Operations

#### Pre-commit Hook:
```bash
#!/bin/bash
# .git/hooks/pre-commit

# Validate JSON syntax
for file in $(git diff --cached --name-only --diff-filter=ACM | grep '\.json$'); do
  if ! python -m json.tool "$file" > /dev/null 2>&1; then
    echo "Error: $file contains invalid JSON"
    exit 1
  fi
done

# Check for sensitive data
if grep -r "password\|secret\|key" workflows/ --include="*.json"; then
  echo "Warning: Potential sensitive data detected"
  read -p "Continue anyway? (y/N): " -n 1 -r
  echo
  if [[ ! $REPLY =~ ^[Yy]$ ]]; then
    exit 1
  fi
fi
```

## Automated Backup Solutions

### 1. Scheduled Workflow Backups

#### Backup Workflow Template:
```json
{
  "name": "Daily Workflow Backup",
  "nodes": [
    {
      "parameters": {
        "rule": {
          "interval": [
            {
              "field": "cronExpression",
              "expression": "0 2 * * *"
            }
          ]
        }
      },
      "name": "Daily Backup Trigger",
      "type": "n8n-nodes-base.cron"
    },
    {
      "parameters": {
        "url": "http://localhost:5678/api/v1/workflows",
        "options": {
          "headers": {
            "Authorization": "Bearer {{$credentials.n8nApi.token}}"
          }
        }
      },
      "name": "Get All Workflows",
      "type": "n8n-nodes-base.httpRequest"
    },
    {
      "parameters": {
        "operation": "write",
        "fileName": "workflows-backup-{{$now.format('YYYY-MM-DD-HH-mm-ss')}}.json",
        "data": "={{JSON.stringify($json, null, 2)}}"
      },
      "name": "Save Backup File",
      "type": "n8n-nodes-base.files"
    }
  ]
}
```

### 2. Cloud Storage Integration

#### Google Drive Backup:
```json
{
  "parameters": {
    "operation": "upload",
    "fileName": "n8n-backup-{{$now.format('YYYY-MM-DD')}}.json",
    "data": "={{$json.backupData}}",
    "options": {
      "folderId": "your-backup-folder-id"
    }
  },
  "name": "Upload to Google Drive",
  "type": "n8n-nodes-base.googleDrive"
}
```

#### AWS S3 Backup:
```json
{
  "parameters": {
    "operation": "upload",
    "bucketName": "n8n-backups",
    "fileName": "workflows/{{$now.format('YYYY/MM/DD')}}/backup.json",
    "data": "={{$json.backupData}}"
  },
  "name": "Upload to S3",
  "type": "n8n-nodes-base.awsS3"
}
```

### 3. Database Backup Automation

#### PostgreSQL Backup Script:
```bash
#!/bin/bash
# backup-db.sh

BACKUP_DIR="/backups/n8n"
DATE=$(date +%Y%m%d_%H%M%S)
DB_NAME="n8n_production"

# Create backup directory
mkdir -p $BACKUP_DIR

# Create database backup
pg_dump $DB_NAME > $BACKUP_DIR/n8n_db_$DATE.sql

# Compress backup
gzip $BACKUP_DIR/n8n_db_$DATE.sql

# Upload to cloud storage
aws s3 cp $BACKUP_DIR/n8n_db_$DATE.sql.gz s3://n8n-backups/database/

# Clean up old backups (keep last 30 days)
find $BACKUP_DIR -name "*.sql.gz" -mtime +30 -delete

echo "Backup completed: n8n_db_$DATE.sql.gz"
```

## Best Practices

### 1. Version Control Best Practices

#### Workflow Naming:
- Use descriptive names: `customer-onboarding-automation`
- Include version numbers: `email-workflow-v2.1`
- Add environment prefix: `prod-data-sync`, `dev-test-workflow`

#### Documentation:
```json
{
  "name": "Customer Onboarding Workflow",
  "version": "2.1.0",
  "description": "Automates customer onboarding process",
  "author": "Development Team",
  "lastModified": "2024-01-15",
  "dependencies": [
    "Gmail API",
    "Google Sheets API",
    "Slack API"
  ],
  "environment": "production",
  "tags": ["customer", "onboarding", "automation"]
}
```

### 2. Backup Scheduling

#### Recommended Schedule:
- **Development**: Every commit
- **Staging**: Daily at 2 AM
- **Production**: Every 6 hours + before deployments
- **Critical Workflows**: Before any modifications

#### Retention Policy:
- **Daily Backups**: Keep for 30 days
- **Weekly Backups**: Keep for 12 weeks
- **Monthly Backups**: Keep for 12 months
- **Yearly Backups**: Keep indefinitely

### 3. Security Considerations

#### Sensitive Data Handling:
```json
{
  "credentials": {
    "example": "{{$credentials.apiKey}}"
  },
  "secrets": {
    "example": "{{$env.SECRET_VALUE}}"
  }
}
```

#### Backup Encryption:
```bash
# Encrypt backup files
gpg --symmetric --cipher-algo AES256 workflow-backup.json

# Decrypt backup files
gpg --decrypt workflow-backup.json.gpg > workflow-backup.json
```

## Recovery Procedures

### 1. Workflow Recovery

#### From n8n History:
1. Open workflow in n8n
2. Go to "History" tab
3. Select desired version
4. Click "Restore"
5. Test restored workflow

#### From Exported Files:
1. Open n8n interface
2. Click "Import from File"
3. Select backup JSON file
4. Review imported workflow
5. Activate if needed

#### From Git Repository:
```bash
# Restore specific workflow
git checkout HEAD~1 -- workflows/production/email-automation.json

# Restore entire workflow set
git checkout HEAD~1 -- workflows/

# Restore from specific commit
git checkout abc1234 -- workflows/production/
```

### 2. Database Recovery

#### PostgreSQL Recovery:
```bash
# Stop n8n service
sudo systemctl stop n8n

# Restore database
psql n8n_db < backup_file.sql

# Start n8n service
sudo systemctl start n8n
```

#### SQLite Recovery:
```bash
# Stop n8n service
sudo systemctl stop n8n

# Replace database file
cp backup_file.db n8n.db

# Start n8n service
sudo systemctl start n8n
```

### 3. Complete Environment Recovery

#### Disaster Recovery Checklist:
1. **Assess Damage**: Determine scope of data loss
2. **Stop Services**: Prevent further data corruption
3. **Restore Database**: Restore from most recent backup
4. **Restore Workflows**: Import workflow files
5. **Restore Credentials**: Reconfigure API credentials
6. **Test Functionality**: Verify all workflows work
7. **Monitor**: Watch for issues in the next 24 hours

## Monitoring and Alerts

### 1. Backup Monitoring

#### Backup Success Alerts:
```json
{
  "name": "Backup Success Notification",
  "nodes": [
    {
      "parameters": {
        "message": "✅ Daily backup completed successfully",
        "channel": "#alerts"
      },
      "name": "Notify Success",
      "type": "n8n-nodes-base.slack"
    }
  ]
}
```

#### Backup Failure Alerts:
```json
{
  "name": "Backup Failure Alert",
  "nodes": [
    {
      "parameters": {
        "message": "🚨 Backup failed! Manual intervention required",
        "channel": "#critical-alerts"
      },
      "name": "Alert Failure",
      "type": "n8n-nodes-base.slack"
    }
  ]
}
```

### 2. Health Checks

#### Workflow Health Monitoring:
```bash
#!/bin/bash
# health-check.sh

# Check if n8n is running
if ! pgrep -f "n8n" > /dev/null; then
  echo "ALERT: n8n service is down"
  exit 1
fi

# Check database connectivity
if ! psql -d n8n_db -c "SELECT 1;" > /dev/null 2>&1; then
  echo "ALERT: Database connection failed"
  exit 1
fi

# Check recent workflow executions
RECENT_FAILURES=$(psql -d n8n_db -t -c "SELECT COUNT(*) FROM execution_entity WHERE finished = false AND started_at < NOW() - INTERVAL '1 hour';")

if [ "$RECENT_FAILURES" -gt 5 ]; then
  echo "ALERT: Too many failed executions"
  exit 1
fi

echo "Health check passed"
```

## Conclusion

Proper backup and versioning strategies are essential for maintaining reliable n8n automation systems. By implementing these practices:

- **Protect your workflows** from data loss and corruption
- **Enable safe collaboration** between team members
- **Facilitate easy recovery** from disasters
- **Maintain audit trails** for compliance requirements
- **Support continuous deployment** practices

### Key Takeaways

1. **Use built-in versioning** for quick rollbacks
2. **Implement Git-based version control** for team collaboration
3. **Automate backup processes** to ensure consistency
4. **Test recovery procedures** regularly
5. **Monitor backup success** with alerts
6. **Secure sensitive data** in backups
7. **Document everything** for future reference

### Next Steps

1. **Audit your current backup strategy**
2. **Implement automated backups** for critical workflows
3. **Set up version control** for your workflow repository
4. **Test recovery procedures** in a safe environment
5. **Train your team** on backup and recovery processes
6. **Monitor and improve** your backup strategy continuously

Remember: The best backup strategy is the one you actually use and test regularly!
