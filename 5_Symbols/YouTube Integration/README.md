# YouTube Integration - Channel Statistics Workflow

This n8n workflow demonstrates how to automatically monitor and report YouTube channel statistics using the YouTube API and Telegram notifications.

## Workflow Overview

The workflow fetches YouTube channel statistics and sends them to a Telegram channel with formatted metrics and calculated ratios.

## Workflow Components

### 1. Triggers (Entry Points)

#### Manual Trigger
- **Node**: "When clicking 'Execute workflow'"
- **Type**: `n8n-nodes-base.manualTrigger`
- **Purpose**: Allows manual execution of the workflow for testing or on-demand stats retrieval

#### Schedule Trigger
- **Node**: "Schedule Trigger"
- **Type**: `n8n-nodes-base.scheduleTrigger`
- **Schedule**: Daily at 6:00 AM (`triggerAtHour: 6`)
- **Purpose**: Automatically runs the workflow every day to track channel growth

### 2. Data Source

#### YouTube Channel API
- **Node**: "Get a channel"
- **Type**: `n8n-nodes-base.youTube`
- **Operation**: `get` (retrieves channel information)
- **Channel ID**: `UCSJyG3bTM7lnjMIZcV8C4OQ`
- **Authentication**: YouTube OAuth2 API credentials
- **Purpose**: Fetches current channel statistics from YouTube API

### 3. Data Processing & Output

#### Telegram Notification
- **Node**: "Send a text message"
- **Type**: `n8n-nodes-base.telegram`
- **Chat ID**: `-1002793496878` (Telegram group/channel)
- **Purpose**: Sends formatted statistics to a Telegram channel

## Data Flow

```
Manual Trigger ──┐
                 ├──> YouTube API ──> Telegram Notification
Schedule Trigger ──┘
```

## Key Statistics Retrieved

The workflow extracts and reports the following metrics:

1. **View Count**: Total views across all videos (`$json.statistics.viewCount`)
2. **Subscriber Count**: Current subscriber count (`$json.statistics.subscriberCount`)
3. **Video Count**: Total number of videos uploaded (`$json.statistics.videoCount`)
4. **Subscriber-to-Video Ratio**: Calculated metric (`Math.round($json.statistics.subscriberCount / $json.statistics.videoCount)`)

## Telegram Message Format

The notification includes:
- Channel URL reference
- Formatted statistics with emojis
- Calculated subscriber-to-video ratio
- Motivational messaging about channel quality

## Authentication Requirements

### YouTube API Setup
1. **Google Cloud Console**: Create a project and enable YouTube Data API v3
2. **OAuth2 Credentials**: Set up OAuth2 credentials for YouTube access
3. **n8n Credentials**: Configure "YouTube account" credentials in n8n

### Telegram Bot Setup
1. **Bot Creation**: Create a Telegram bot via @BotFather
2. **Bot Token**: Obtain the bot token
3. **Chat ID**: Get the target chat/group ID
4. **n8n Credentials**: Configure "Telegram account" credentials in n8n

## Channel ID Extraction

To find a YouTube channel ID from a URL like `https://www.youtube.com/@RifatErdemSahin`:

1. Open the channel page in a web browser
2. Right-click and select "View Page Source"
3. Search for "channelId" in the HTML source
4. Look for: `<meta itemprop="channelId" content="UCxxxxxxxxxxxxxxxxxxxxxx">`
5. Extract the value from the "content" attribute

## Workflow Configuration

### Settings
- **Execution Order**: v1 (sequential execution)
- **Active**: true (workflow is enabled)
- **Tags**: "youtubepromotion", "monitoring"

### Node Positions
The workflow uses a logical layout with:
- Triggers on the left
- Data processing in the center
- Output on the right

## Use Cases

This workflow is ideal for:

1. **Channel Growth Monitoring**: Daily tracking of subscriber and view growth
2. **Performance Analytics**: Calculating engagement ratios and metrics
3. **Automated Reporting**: Regular updates to team channels or stakeholders
4. **Growth Milestone Alerts**: Notifications when specific thresholds are reached

## Extensions and Modifications

Potential enhancements:

1. **Historical Tracking**: Store statistics in a database for trend analysis
2. **Multiple Channels**: Monitor several YouTube channels simultaneously
3. **Conditional Alerts**: Send notifications only when specific milestones are reached
4. **Dashboard Integration**: Feed data to visualization tools
5. **Cross-Platform**: Extend to other social media platforms

## Technical Notes

- **API Limits**: YouTube API has daily quotas; monitor usage for high-frequency workflows
- **Error Handling**: Consider adding error handling nodes for API failures
- **Data Validation**: Verify that statistics data exists before processing
- **Timezone**: Schedule trigger uses system timezone for execution timing

## Troubleshooting

Common issues and solutions:

1. **Authentication Errors**: Verify OAuth2 credentials and permissions
2. **Channel Not Found**: Confirm channel ID is correct and channel is public
3. **Telegram Delivery**: Ensure bot has permissions to send messages to target chat
4. **API Quotas**: Check YouTube API quota usage in Google Cloud Console

