{
  "nodes": [
    {
      "parameters": {
        "httpMethod": "POST",
        "path": "contact-form-submission",
        "options": {}
      },
      "id": "18e6a105-0275-4c60-a86d-3e6f9661c470",
      "name": "Catch Contact Form",
      "type": "n8n-nodes-base.webhook",
      "typeVersion": 1,
      "position": [
        860,
        380
      ],
      "webhookId": "b1a2e3f4-5678-90ab-cdef-1234567890ab"
    },
    {
      "parameters": {
        "operation": "append",
        "documentId": {
          "__rl": true,
          "value": "YOUR_SPREADSHEET_ID_HERE",
          "mode": "url"
        },
        "sheetName": {
          "__rl": true,
          "value": "gid=0",
          "mode": "url"
        },
        "fields": {
          "values": [
            {
              "name": "={{ $json.body.name }}",
              "email": "={{ $json.body.email }}",
              "message": "={{ $json.body.message }}",
              "receivedAt": "={{ $now.toFormat('dd/MM/yyyy HH:mm') }}"
            }
          ]
        },
        "options": {}
      },
      "id": "e23fa282-50bd-4770-b6f7-7b96e147d33d",
      "name": "Add to Google Sheet",
      "type": "n8n-nodes-base.googleSheets",
      "typeVersion": 4.2,
      "position": [
        1080,
        380
      ],
      "credentials": {
        "googleSheetsOAuth2Api": {
          "id": "YOUR_GOOGLE_CREDENTIALS_ID",
          "name": "Google Sheets account"
        }
      }
    },
    {
      "parameters": {
        "text": "=New contact form submission from *{{ $json.body.name }}*!\n>Email: {{ $json.body.email }}\n>Message: _{{ $json.body.message }}_",
        "options": {}
      },
      "id": "c9c2f6d5-a38f-4ac6-b7e6-28562fca80de",
      "name": "Notify Team on Slack",
      "type": "n8n-nodes-base.slack",
      "typeVersion": 3.1,
      "position": [
        1300,
        380
      ],
      "credentials": {
        "slackOAuth2Api": {
          "id": "YOUR_SLACK_CREDENTIALS_ID",
          "name": "Slack account"
        }
      }
    }
  ],
  "connections": {
    "Catch Contact Form": {
      "main": [
        [
          {
            "node": "Add to Google Sheet",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Add to Google Sheet": {
      "main": [
        [
          {
            "node": "Notify Team on Slack",
            "type": "main",
            "index": 0
          }
        ]
      ]
    }
  }
}