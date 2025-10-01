# Project - Automated Discord/Slack Notifications

## Project Overview

This project demonstrates how to create automated notification workflows for Discord and Slack using n8n. You'll learn how to connect your Discord or Slack account, create workflows that send custom messages, and implement proper error handling and message formatting.

## Learning Objectives

By completing this project, you will:

- **Connect Discord/Slack accounts** to n8n using proper credentials
- **Create manual trigger workflows** for on-demand notifications
- **Implement conditional logic** for different message types
- **Format rich messages** with embeds, attachments, and styling
- **Handle errors gracefully** with proper error reporting
- **Customize notifications** with dynamic content and timestamps

## Prerequisites

Before starting this project, ensure you have:

- An active n8n instance (self-hosted or cloud)
- A Discord server where you can create webhooks
- A Slack workspace where you can create apps
- Basic understanding of n8n nodes and workflow concepts

## Project Structure

This project includes:

- `discord-notifications-workflow.json` - Complete Discord notification workflow
- `slack-notifications-workflow.json` - Complete Slack notification workflow
- `README.md` - This comprehensive guide

## Part 1: Discord Notifications

### Setting Up Discord Credentials

#### Step 1: Create a Discord Webhook

1. **Open Discord** and navigate to your server
2. **Right-click on a channel** where you want to receive notifications
3. **Select "Edit Channel"** from the context menu
4. **Go to "Integrations"** tab
5. **Click "Create Webhook"**
6. **Copy the webhook URL** (keep this secure!)

#### Step 2: Configure Discord Credentials in n8n

1. **Open n8n** and go to **Credentials**
2. **Click "Create New Credential"**
3. **Search for "Discord"** and select **"Discord Webhook"**
4. **Enter your credential details:**
   ```
   Credential Name: Discord Webhook Credentials
   Webhook URL: [paste your Discord webhook URL]
   ```
5. **Click "Test"** to verify the connection
6. **Save** the credential

### Discord Workflow Features

The Discord workflow includes:

#### 1. **Manual Trigger**
- Starts the workflow when manually executed
- Perfect for testing and on-demand notifications

#### 2. **Default Values Setup**
- Sets default message content
- Configures bot username and avatar
- Defines message type (info/error)

#### 3. **Conditional Message Formatting**
- **Error messages**: Red embed with 🚨 icon
- **Success messages**: Green embed with ✅ icon
- Dynamic content based on message type

#### 4. **Rich Discord Embeds**
- **Color-coded embeds** (red for errors, green for success)
- **Custom titles and descriptions**
- **Timestamp information**
- **Footer with n8n branding**

#### 5. **Response Formatting**
- Success/error status reporting
- Execution timestamp
- Response code validation

### Running the Discord Workflow

1. **Import** `discord-notifications-workflow.json` into n8n
2. **Update the credential reference** in the "Send Discord Webhook" node
3. **Click "Execute Workflow"** to test
4. **Check your Discord channel** for the notification

### Customizing Discord Messages

#### Modify Message Content:
```javascript
// In the "Set Default Values" node
customMessage: "Your custom message here - {{$now}}"
```

#### Change Message Type:
```javascript
// Set to "error" for error styling, "info" for success styling
messageType: "error"
```

#### Customize Bot Appearance:
```javascript
username: "Your Custom Bot Name"
avatarUrl: "https://your-image-url.com/bot-avatar.png"
```

## Part 2: Slack Notifications

### Setting Up Slack Credentials

#### Step 1: Create a Slack App

1. **Go to** [api.slack.com/apps](https://api.slack.com/apps)
2. **Click "Create New App"**
3. **Choose "From scratch"**
4. **Enter app details:**
   ```
   App Name: n8n Notifications
   Development Slack Workspace: [select your workspace]
   ```
5. **Click "Create App"**

#### Step 2: Configure Bot Permissions

1. **Go to "OAuth & Permissions"** in your app settings
2. **Add the following Bot Token Scopes:**
   - `chat:write` - Send messages
   - `chat:write.public` - Send to public channels
   - `channels:read` - List channels
3. **Click "Install to Workspace"**
4. **Copy the Bot User OAuth Token** (starts with `xoxb-`)

#### Step 3: Configure Slack Credentials in n8n

1. **Open n8n** and go to **Credentials**
2. **Click "Create New Credential"**
3. **Search for "Slack"** and select **"Slack API"**
4. **Enter your credential details:**
   ```
   Credential Name: Slack API Credentials
   Access Token: [paste your Bot User OAuth Token]
   ```
5. **Click "Test"** to verify the connection
6. **Save** the credential

### Slack Workflow Features

The Slack workflow includes:

#### 1. **Manual Trigger**
- Initiates the workflow manually
- Allows for testing and custom notifications

#### 2. **Default Configuration**
- Sets default channel, username, and emoji
- Configures message type and content
- Defines custom message text

#### 3. **Message Type Handling**
- **Error messages**: Red color with ❌ icon
- **Success messages**: Green color with ✅ icon
- Dynamic styling based on message type

#### 4. **Rich Slack Attachments**
- **Color-coded attachments** for visual distinction
- **Structured fields** with titles and values
- **Timestamp information**
- **Source attribution**

#### 5. **Error Handling**
- Automatic error alert to dedicated channel
- Detailed error information
- Timestamp and workflow identification

### Running the Slack Workflow

1. **Import** `slack-notifications-workflow.json` into n8n
2. **Update the credential reference** in Slack nodes
3. **Modify the default channel** if needed
4. **Click "Execute Workflow"** to test
5. **Check your Slack channel** for the notification

### Customizing Slack Messages

#### Change Target Channel:
```javascript
// In the "Set Default Values" node
channel: "#your-channel-name"
```

#### Modify Message Content:
```javascript
customMessage: "Your custom Slack message - {{$now}}"
```

#### Customize Bot Appearance:
```javascript
username: "Your Custom Bot"
emoji: ":custom_emoji:"
```

#### Update Error Alert Channel:
```javascript
// In the "Send Error Alert" node
channel: "#alerts"  // Change to your alerts channel
```

## Advanced Features

### 1. Dynamic Content

Both workflows support dynamic content using n8n expressions:

```javascript
// Current timestamp
"Sent at {{$now}}"

// Current date and time
"Executed on {{$now.format('YYYY-MM-DD HH:mm:ss')}}"

// User information (if available)
"Hello {{$json.userName || 'User'}}"

// Conditional content
"{{$json.messageType === 'error' ? '❌ Error' : '✅ Success'}}"
```

### 2. Message Templates

Create reusable message templates:

#### Discord Template:
```javascript
{
  "title": "🚨 System Alert",
  "description": "{{$json.message}}",
  "color": "{{$json.messageType === 'error' ? '16711680' : '65280'}}",
  "footer": "Automated by n8n",
  "timestamp": "{{$now}}"
}
```

#### Slack Template:
```javascript
{
  "color": "{{$json.messageType === 'error' ? 'danger' : 'good'}}",
  "title": "{{$json.messageType === 'error' ? 'Error' : 'Success'}} Notification",
  "fields": [
    {
      "title": "Message",
      "value": "{{$json.message}}",
      "short": false
    },
    {
      "title": "Timestamp",
      "value": "{{$now}}",
      "short": true
    }
  ]
}
```

### 3. Error Handling

Both workflows include comprehensive error handling:

- **Try-catch logic** for API calls
- **Fallback notifications** for critical errors
- **Detailed error reporting** with context
- **Automatic retry mechanisms** (configurable)

## Integration Examples

### 1. Connect to Other Services

Extend these workflows by adding triggers from other services:

```javascript
// GitHub webhook trigger
// Send Discord/Slack notification when PR is created

// Email trigger
// Notify team when important email arrives

// Schedule trigger
// Send daily/weekly reports
```

### 2. Multi-Channel Notifications

Send the same message to multiple channels:

```javascript
// Send to multiple Discord channels
// Send to multiple Slack workspaces
// Send to both Discord and Slack simultaneously
```

### 3. Conditional Notifications

Send different messages based on conditions:

```javascript
// Different messages for different environments
// Different channels for different severity levels
// Different formats for different message types
```

## Troubleshooting

### Common Discord Issues

#### "Invalid Webhook" Error:
- Verify webhook URL is correct
- Ensure webhook hasn't been deleted
- Check if webhook has proper permissions

#### "Message Not Appearing":
- Verify channel permissions
- Check if bot has send message permissions
- Ensure webhook is properly configured

### Common Slack Issues

#### "Invalid Auth Token" Error:
- Verify Bot User OAuth Token is correct
- Ensure token has required scopes
- Check if app is installed in workspace

#### "Channel Not Found" Error:
- Verify channel name is correct (include #)
- Ensure bot is invited to the channel
- Check channel permissions

#### "Missing Scope" Error:
- Add required scopes in Slack app settings
- Reinstall app to workspace
- Verify OAuth token includes new scopes

### General Troubleshooting

#### Test Credentials:
1. Go to **Credentials** in n8n
2. Select your Discord/Slack credential
3. Click **"Test"** to verify connection
4. Check for error messages

#### Check Workflow Execution:
1. Go to **Executions** in n8n
2. Find your workflow execution
3. Review each node's output
4. Check for error messages

#### Verify Node Configuration:
1. Check each node's parameters
2. Verify credential references
3. Test expressions individually
4. Validate data flow between nodes

## Security Best Practices

### 1. Credential Management
- **Never share webhook URLs** or OAuth tokens
- **Use environment variables** for sensitive data
- **Regularly rotate credentials** for security
- **Limit bot permissions** to minimum required

### 2. Channel Security
- **Use private channels** for sensitive notifications
- **Limit bot access** to necessary channels only
- **Monitor bot activity** for unusual behavior
- **Set up audit logs** for notification tracking

### 3. Message Content
- **Sanitize user input** before sending
- **Avoid sending sensitive data** in notifications
- **Use appropriate channels** for different message types
- **Implement rate limiting** for high-volume notifications

## Extending the Project

### 1. Add More Message Types
- **Warning messages** with yellow/orange styling
- **Info messages** with blue styling
- **Custom message types** with specific formatting

### 2. Implement Scheduling
- **Daily reports** at specific times
- **Weekly summaries** with aggregated data
- **Event-based notifications** triggered by external events

### 3. Add Analytics
- **Track notification delivery** rates
- **Monitor response times** for different channels
- **Generate reports** on notification effectiveness

### 4. Create Templates
- **Pre-built message templates** for common scenarios
- **Customizable templates** with variables
- **Template library** for different use cases

## Conclusion

This project provides a solid foundation for implementing automated notifications in Discord and Slack using n8n. You've learned:

- **How to connect** Discord and Slack accounts securely
- **How to create** manual trigger workflows
- **How to format** rich messages with embeds and attachments
- **How to handle** errors and edge cases
- **How to customize** notifications for your specific needs

### Next Steps

1. **Experiment** with different message formats and styles
2. **Connect** these workflows to other services and triggers
3. **Create** more sophisticated notification logic
4. **Implement** monitoring and analytics for your notifications
5. **Share** your workflows with your team

### Additional Resources

- [Discord Webhook Documentation](https://discord.com/developers/docs/resources/webhook)
- [Slack API Documentation](https://api.slack.com/)
- [n8n Discord Node Documentation](https://docs.n8n.io/integrations/builtin/cli-nodes/n8n-nodes-base.discord/)
- [n8n Slack Node Documentation](https://docs.n8n.io/integrations/builtin/cli-nodes/n8n-nodes-base.slack/)

Happy automating! 🚀
