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

# 📊 Reading Data from Google Sheets

Connecting n8n to your spreadsheets.

---

## 🔑 Google API Credentials

Before you can read from a Google Sheet, you need to set up credentials.

1.  **Create a Google Cloud Project**.
2.  **Enable the Google Sheets API**.
3.  **Configure the OAuth Consent Screen**.
4.  **Create an OAuth 2.0 Client ID**.
5.  **Add the credentials to n8n**.

---

## 🤖 The Demo Workflow

`google-sheets-read-workflow.json`

This workflow demonstrates how to read data from a Google Sheet:

1.  **Set Parameters**: Defines the Spreadsheet ID and range to read.
2.  **Read Google Sheet**: Uses the Google Sheets node to get the data.
3.  **Check if Data Exists**: An `IF` node checks if any rows were returned.
4.  **Process Data**: If data exists, it's processed.
5.  **Handle Empty Response**: If no data, a different path is taken.

---

## ✨ The Google Sheets Node

<div class="columns">
<div>

### Read Operation

- **Document ID**: The ID of your Google Sheet.
- **Sheet Name**: The name of the sheet to read from.
- **Range**: The cells to read (e.g., `A1:B10`).

</div>
<div>

### Options

- **Has Header Row**: Tells n8n to use the first row as keys for the JSON objects.
- **Include Empty Cells**: Choose whether to include empty cells in the output.

</div>
</div>

---

## ✅ Best Practices

- **Use specific ranges** instead of reading the whole sheet.
- **Enable `Has Header Row`** to get nicely formatted JSON.
- **Use a dedicated service account** for production workflows for better security.

---

## 📚 External Resources

- **n8n Google Sheets Node Documentation**: [https://docs.n8n.io/integrations/builtin/cli-nodes/n8n-nodes-base.googlesheets/](https://docs.n8n.io/integrations/builtin/cli-nodes/n8n-nodes-base.googlesheets/)
- **Google Cloud Console**: [https://console.cloud.google.com/](https://console.cloud.google.com/)