Of course\! Let's dive into the most fundamental part of any automation: the **Trigger Node**.

### What is a Trigger Node?

Think of an n8n workflow as a series of dominoes. The **Trigger Node** is the very first domino that you push over to start the chain reaction. It's the "WHEN this happens..." part of your automation.

A workflow can only have **one** Trigger Node. It's the starting point that listens for a specific event—a schedule, a form submission, a new email, a message in Slack—and then starts the workflow, feeding it any data it received.

For your very first trigger, the two simplest and most common are:

1.  **Manual / Start:** You literally click a button to run the workflow. Great for testing.
2.  **Webhook:** The workflow listens at a unique URL for incoming data. This is the most powerful and common way to connect different web services.

We will build our example using the **Webhook Trigger** because it perfectly demonstrates how data enters a workflow from an external source.

-----

### Our Example: A "New Contact Form" Workflow

**The Goal:** When someone submits a contact form on our website, we want to automatically save their details to a Google Sheet and then send a notification to our team's Slack channel.

**The Flow:**
`[Webhook Trigger]` $\rightarrow$ `[Google Sheets Node]` $\rightarrow$ `[Slack Node]`

1.  **Trigger (The "When"):** When a new form is submitted (this sends data to our Webhook URL).
2.  **Action 1:** Add the person's name, email, and message to a new row in Google Sheets.
3.  **Action 2:** Post a message in Slack saying "New contact from [Name]\!".

-----

### The n8n Workflow For It

Here is the JSON code you can copy and paste directly into your n8n canvas to create this example workflow.

```json
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
```

***Note:** You will need to replace `YOUR_SPREADSHEET_ID_HERE` and connect your own Google and Slack credentials for this to work.*

-----

### The "Post-it Note" Explanation

Imagine your workflow is an assembly line, and the data moves along it on a **Post-it Note**.

#### 1\. The Trigger: A Blank Stack of Post-its

  * The **Webhook Trigger** node is like a person standing by a special, magical door (the webhook URL), holding a blank stack of Post-it Notes.
  * They are just waiting. Their only job is to listen for a knock on that door.
  * The workflow is **inactive**. Nothing is happening.

#### 2\. The Event: Someone Knocks\!

  * A user, Alice, fills out your website's contact form and clicks "Submit".
  * Your website's code immediately sends her information to your special webhook URL. This is the "knock on the door".
  * The Webhook Trigger person springs into action\! They grab a **single, fresh Post-it Note** from their stack.
  * On this Post-it, they write down everything they received from the form submission.

#### 3\. Passing the Note to the Next Step

  * The workflow is now **active for Alice's submission**.
  * The Webhook Trigger person takes the Post-it and hands it to the next person in the assembly line: the **Google Sheets Node**.
  * The Google Sheets person looks at the note. Their instructions are: "Take the 'name', 'email', and 'message' fields from this Post-it and add them as a new row in the 'Contact Form' spreadsheet."
  * They do their job, and now Alice's data is safely in your spreadsheet.

#### 4\. The Final Step

  * The Google Sheets person then passes the **exact same Post-it Note** to the final person in the line: the **Slack Node**.
  * The Slack person looks at the note. Their instructions are: "Create a new message that says 'New contact form submission from...' and fill in the blank with the 'name' from the Post-it."
  * They craft the message: "New contact form submission from **Alice**\!" and post it to the `#leads` channel.

#### Conclusion

The workflow for Alice's submission is now complete. The Post-it Note is discarded. The Webhook Trigger person is back at their door, waiting with a fresh stack of blank notes for the next submission.

If another user, Bob, submits the form two seconds later, the **entire process starts over with a brand new, separate Post-it Note** just for Bob. This is how n8n can handle many events at once without getting them mixed up.

The **Trigger Node** is the crucial first step that creates the Post-it Note and starts its journey down your automation assembly line.
