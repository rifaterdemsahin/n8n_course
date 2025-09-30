# 5_Symbols - Practical Projects & Workflows

This folder contains hands-on projects and practical workflows that demonstrate real-world n8n automation scenarios. Each project includes complete workflow files and detailed documentation.

## Overview

The best way to learn n8n is through hands-on practice with real projects. This folder provides a collection of practical workflows that build from basic concepts to advanced automation scenarios.

## Project Structure

Each project folder contains:
- **Workflow JSON files** - Ready-to-import n8n workflows
- **README.md** - Detailed explanation and learning guide
- **Sample data** - Test data for workflow validation (when applicable)
- **Documentation** - Step-by-step implementation guides

## Available Projects

### Project - Simple Data Transformation
**Difficulty:** Beginner  
**Learning Focus:** Basic data manipulation with Set node  
**Files:**
- `set-node-workflow.json` - Complete workflow file
- `README.md` - Comprehensive learning guide

**What You'll Learn:**
- Using the Set node for data transformation
- Basic expression syntax
- Data flow between nodes
- JSON data structure understanding

### Viewing Your Workflow's Data
**Difficulty:** Beginner  
**Learning Focus:** Understanding workflow output and data navigation  
**Files:**
- `data-viewing-workflow.json` - Workflow demonstrating data viewing
- `README.md` - Data interpretation guide

**What You'll Learn:**
- JSON data structure navigation
- Table vs JSON view comparison
- Data output interpretation
- Workflow execution monitoring

### Understanding Credentials
**Difficulty:** Beginner to Intermediate  
**Learning Focus:** Secure credential management for third-party services  
**Files:**
- `credentials-demo-workflow.json` - Comprehensive credential testing workflow
- `README.md` - Complete credential management guide

**What You'll Learn:**
- What credentials are and why they're important
- How to securely add credentials for third-party services
- Best practices for credential security
- Testing and troubleshooting credentials
- Multiple credential types (OAuth2, API Keys, SMTP, etc.)
- Real-world credential management scenarios

### Project - Automated Discord/Slack Notifications
**Difficulty:** Intermediate  
**Learning Focus:** Communication platform integration and notification workflows  
**Files:**
- `discord-notifications-workflow.json` - Complete Discord notification workflow
- `slack-notifications-workflow.json` - Complete Slack notification workflow
- `README.md` - Comprehensive integration guide

**What You'll Learn:**
- Connecting Discord and Slack accounts to n8n
- Creating workflows that send custom messages on manual trigger
- Implementing rich message formatting with embeds and attachments
- Conditional logic for different message types (success/error)
- Error handling and fallback notifications
- Security best practices for communication platforms
- Customizing bot appearance and message content

### Setting up Google API credentials
**Difficulty:** Intermediate  
**Learning Focus:** Google Cloud Platform integration and API credential management  
**Files:**
- `google-sheets-read-workflow.json` - Complete Google Sheets read workflow
- `README.md` - Step-by-step Google API setup guide

**What You'll Learn:**
- Creating and configuring Google Cloud projects
- Setting up OAuth2 credentials for Google APIs
- Enabling and configuring Google Sheets and Drive APIs
- Configuring OAuth consent screen for external applications
- Connecting Google credentials to n8n workflows
- Configuring Google Sheets node to read rows from spreadsheets
- Understanding range notation and data formatting options
- Implementing error handling and data validation
- Security best practices for Google API integration

## Project Categories

### Beginner Projects
- **Data Transformation** - Basic data manipulation
- **Simple Integrations** - Two-service connections
- **Conditional Logic** - Basic IF/Switch implementations
- **Data Formatting** - String and number formatting

### Intermediate Projects
- **Multi-Service Integration** - Complex service connections
- **Communication Platform Integration** - Discord/Slack notifications
- **Google API Integration** - Google Sheets, Drive, and OAuth2 setup
- **Data Processing** - Advanced data manipulation
- **Error Handling** - Robust error management
- **Scheduling** - Time-based automation

### Advanced Projects
- **Enterprise Integration** - Complex business processes
- **Custom Logic** - Advanced conditional processing
- **Performance Optimization** - Efficient workflow design
- **Monitoring & Alerting** - Production-ready monitoring

## How to Use These Projects

### 1. Import Workflows
1. Open your n8n instance
2. Create a new workflow
3. Click "Import from File"
4. Select the project's JSON file
5. Review the imported workflow

### 2. Study the Documentation
1. Read the project's README.md file
2. Understand the workflow's purpose
3. Review each node's configuration
4. Learn about the expressions used

### 3. Execute and Test
1. Run the workflow with sample data
2. Observe the data flow
3. Check outputs in different views
4. Modify parameters to see changes

### 4. Experiment and Modify
1. Add new nodes to extend functionality
2. Modify expressions to change behavior
3. Test with different input data
4. Create variations of the original workflow

## Learning Progression

### Phase 1: Foundation (Beginner)
1. **Simple Data Transformation** - Master basic data manipulation
2. **Data Viewing Techniques** - Understand workflow outputs
3. **Manual Triggers** - Learn workflow execution
4. **Basic Expressions** - Introduction to n8n expressions

### Phase 2: Integration (Intermediate)
1. **Understanding Credentials** - Master secure credential management
2. **Service Connections** - Connect external services
3. **Data Synchronization** - Keep systems in sync
4. **Error Handling** - Build robust workflows

### Phase 3: Automation (Advanced)
1. **Scheduled Workflows** - Time-based automation
2. **Event-Driven Automation** - Reactive workflows
3. **Complex Business Logic** - Multi-step processes
4. **Production Deployment** - Real-world implementation

## Best Practices for Projects

### Workflow Design
- **Clear Naming** - Use descriptive names for nodes and workflows
- **Logical Flow** - Arrange nodes in logical order
- **Documentation** - Add comments explaining complex logic
- **Error Handling** - Include error management from the start

### Testing Strategy
- **Sample Data** - Test with realistic data sets
- **Edge Cases** - Test boundary conditions
- **Error Scenarios** - Verify error handling works
- **Performance** - Monitor execution time and resources

### Maintenance
- **Version Control** - Track workflow changes
- **Backup Strategy** - Regular workflow backups
- **Monitoring** - Set up execution monitoring
- **Documentation Updates** - Keep documentation current

## Contributing New Projects

When adding new projects:

### Project Requirements
- **Clear Purpose** - Well-defined learning objective
- **Complete Documentation** - Comprehensive README
- **Tested Workflow** - Verified functionality
- **Sample Data** - Realistic test scenarios

### Documentation Standards
- **Learning Objectives** - What students will learn
- **Prerequisites** - Required knowledge/skills
- **Step-by-Step Guide** - Implementation instructions
- **Troubleshooting** - Common issues and solutions

### Quality Assurance
- **Functionality Testing** - Verify workflow works correctly
- **Documentation Review** - Ensure clarity and completeness
- **Code Review** - Check expressions and logic
- **User Testing** - Validate with target audience

## Integration with Course Structure

These projects directly support:
- **`1_Real/`** - Achieving key results through hands-on practice
- **`4_Formula/`** - Applying expression knowledge in real scenarios
- **`6_Semblance/`** - Visual examples of workflow results
- **`7_Testing/`** - Validating project implementations

## Resources

### n8n Resources
- [n8n Documentation](https://docs.n8n.io/)
- [n8n Community Forum](https://community.n8n.io/)
- [n8n Node Reference](https://docs.n8n.io/integrations/)

### Learning Resources
- [Workflow Templates](https://n8n.io/workflows/)
- [Community Examples](https://github.com/n8n-io/n8n/tree/master/packages/cli/src/workflows)
- [Video Tutorials](https://www.youtube.com/c/n8nio)

This collection of practical projects provides the hands-on experience needed to master n8n automation and build real-world automation solutions.

