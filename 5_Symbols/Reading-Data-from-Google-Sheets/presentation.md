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

# 🔑 Setting up Google API Credentials - A Step-by-Step Guide

---

## ✅ Prerequisites

- 🇬 Google account
- ☁️ Access to Google Cloud Console
- 🤖 n8n instance
- 🤔 Basic understanding of APIs and OAuth2

---

## 1️⃣ Step 1: Create a Google Cloud Project

1.  ☁️ Access Google Cloud Console.
2.  ➕ Create a new project.
3.  🆔 Note the Project ID.

---

## 2️⃣ Step 2: Enable Required APIs

1.  Navigate to "APIs & Services" -> "Library".
2.  ✅ Enable "Google Sheets API".
3.  ✅ Enable "Google Drive API" (recommended).

---

## 3️⃣ Step 3: Configure OAuth Consent Screen

1.  Go to "OAuth consent screen".
2.  🧑‍🤝‍🧑 Choose "External" user type.
3.  📝 Fill in app information.
4.  ➕ Add scopes: `https://www.googleapis.com/auth/spreadsheets` and `https://www.googleapis.com/auth/drive`.
5.  🧑‍💻 Add test users.

---

## 4️⃣ Step 4: Create OAuth2 Credentials

1.  Go to "Credentials".
2.  ➕ Create "OAuth client ID".
3.  🌐 Select "Web application".
4.  ➡️ Add authorized redirect URIs for your n8n instance.
5.  🤫 Copy the Client ID and Client Secret.

---

## 5️⃣ Step 5: Configure Credentials in n8n

1.  In n8n, go to "Credentials" and create a new "Google Sheets OAuth2 API" credential.
2.  📝 Enter the Client ID, Client Secret, and scopes.
3.  🔗 Connect your Google account.

---

## 6️⃣ Step 6: Test the Connection

1.  ➕ Create a new workflow with a Google Sheets node.
2.  ⚙️ Configure the node to read from a sheet.
3.  ▶️ Execute the workflow and verify that data is retrieved.

---

## 📊 Google Sheets Integration

- **Operations**: Read, Write, Update, Delete, Create.
- **Range Notation**: `A1`, `A1:B10`, `A:A`, `1:1`, `A:Z`.
- **Data Format**: With or without headers.

---

## 🛠️ Troubleshooting

- "Invalid Credentials"
- "Access Denied"
- "Spreadsheet Not Found"
- "Range Not Found"
- "Quota Exceeded"

---

## 🔒 Security Best Practices

- 🤫 Securely store credentials.
- 👍 Use the principle of least privilege for scopes.
- 📊 Monitor API usage and access logs.
