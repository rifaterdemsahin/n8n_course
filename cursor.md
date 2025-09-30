# n8n Course Project Structure

This project contains educational materials and workflows for learning n8n automation. The structure is organized to provide a comprehensive learning experience with practical examples and structured OKR (Objectives and Key Results) tracking.

## Project Overview

This is an n8n course project designed to teach automation concepts through hands-on examples, structured learning materials, and clear progress tracking using OKR methodology.

## Directory Structure

```
n8n_course/
├── 1_Real/                              # OKR Management & Course Objectives
│   ├── objective.md                     # Main course objective
│   ├── keyresults1.md                   # Overview of all key results
│   ├── keyresults1.md (individual)      # KR1: Foundation Mastery
│   ├── keyresults2.md                   # KR2: Advanced Node Proficiency
│   ├── keyresults3.md                   # KR3: Real-World Project Implementation
│   ├── keyresults4.md                   # KR4: Production Readiness
│   └── README.md                        # OKR system explanation
├── 2_Environment/                       # Environment Setup & Configuration
│   └── README.md                        # Environment setup guides
├── 3_Imaginary/                         # Theoretical Concepts & Planning
│   └── README.md                        # Course theory and planning docs
├── 4_Formula/                           # Formulas, Expressions & Calculations
│   └── README.md                        # n8n expression guides and formulas
├── 5_Symbols/                           # Practical Projects & Workflows
│   ├── Project - Simple Data Transformation/
│   │   ├── README.md                    # Detailed explanation of the workflow
│   │   └── set-node-workflow.json      # n8n workflow file
│   ├── Viewing Your Workflow's Data/
│   │   ├── README.md                    # Data viewing techniques guide
│   │   └── data-viewing-workflow.json  # Data viewing workflow
│   └── README.md                        # Projects overview and index
├── 6_Semblance/                         # Visual Examples & Templates
│   └── README.md                        # Visual examples and templates
├── 7_Testing/                           # Testing & Quality Assurance
│   └── README.md                        # Testing strategies and QA guides
├── outline.md                           # Course outline and curriculum
├── README.md                            # Course introduction and overview
└── cursor.md                            # This file - project structure guide
```

## How to Use This Project

### 1. OKR Management (`1_Real/`)
- **`objective.md`**: Main course objective and success criteria
- **`keyresults1.md`**: Overview linking to all individual key results
- **Individual KR files**: Detailed breakdown of each learning milestone
- **`README.md`**: Explanation of OKR system and progress tracking

### 2. Environment Setup (`2_Environment/`)
- **Setup guides**: n8n Cloud and self-hosted installation
- **Configuration**: Environment variables, credentials setup
- **`README.md`**: Complete environment setup documentation

### 3. Theoretical Concepts (`3_Imaginary/`)
- **Course planning**: Curriculum design and learning objectives
- **Conceptual materials**: Theory behind automation principles
- **`README.md`**: Theoretical foundations and course philosophy

### 4. Formulas & Expressions (`4_Formula/`)
- **Expression guides**: n8n expression syntax and examples
- **Calculation formulas**: Common automation calculations
- **`README.md`**: Complete reference for n8n expressions

### 5. Practical Projects (`5_Symbols/`)
Each project folder contains:
- **Workflow JSON files**: Ready-to-import n8n workflows
- **README.md**: Detailed explanations with Mermaid diagrams, architecture overview, implementation steps, and learning objectives

#### Current Projects:

##### Foundation Projects
- **Project - Simple Data Transformation**: Basic data manipulation using Set node
- **Viewing Your Workflow's Data**: Understanding JSON data structure and navigation
- **Understanding Credentials**: Secure credential management for third-party services
- **Working with Variables**: Global vs execution variables and expressions

##### Logic and Control Flow
- **Lecture 17 - The IF Node**: Adding conditional logic to workflows
- **The Switch Node**: Handling multiple conditions and routing data
- **The Merge Node**: Combining data from different workflow branches
- **Understanding Data Loops**: Split in Batches node and iteration patterns

##### Real-World Integration Projects
- **Project - Automated Discord/Slack Notifications**: Communication platform integration
- **Setting up Google API credentials**: Google Cloud Platform and OAuth2 setup
- **Writing Data to Google Sheets**: Appending and updating spreadsheet data
- **Practical Real-World Projects**: Daily weather reports with Cron triggers

##### Advanced Topics
- **Rate Limits in Real World**: Handling API rate limits and error recovery
- **Learn to Backup and Version Your Workflows**: Version control and backup strategies
- **Handling Errors in Your Workflows**: Error workflows and debugging techniques
- **Risk Management**: Production deployment and risk mitigation
- **Exploring Community Nodes**: Extending n8n functionality with custom nodes

##### Course Completion
- **Course Wrap-Up & Your Automation Journey**: Recap, next steps, and community resources

### 6. Visual Examples (`6_Semblance/`)
- **Templates**: Visual workflow templates and examples
- **Screenshots**: Interface guides and visual documentation
- **`README.md`**: Visual learning resources and templates

### 7. Testing & QA (`7_Testing/`)
- **Testing strategies**: How to test and validate workflows
- **Quality assurance**: Best practices for reliable automation
- **`README.md`**: Testing methodologies and QA procedures

## Getting Started

1. **Read the Course Materials**: Start with `n8n_course/README.md` for course overview
2. **Follow the Outline**: Use `n8n_course/outline.md` to understand the learning path
3. **Practice with Projects**: Import workflow JSON files into your n8n instance
4. **Study the Documentation**: Read the README files in each project folder for detailed explanations

## Importing Workflows

To use the workflow examples:

1. Open your n8n instance
2. Create a new workflow
3. Click the "Import from File" option
4. Select the desired `.json` file from the project folders
5. The workflow will be imported and ready to run

## Learning Path

1. **Start with Course Materials**: Read the main course content first
2. **Follow Sequential Projects**: Work through projects in the suggested order
3. **Experiment**: Modify the imported workflows to understand how changes affect behavior
4. **Read Documentation**: Each project includes detailed explanations of concepts and techniques

## Project Philosophy

This course emphasizes:
- **Hands-on Learning**: Every concept is demonstrated with working examples
- **Progressive Complexity**: Starting with simple concepts and building to advanced topics
- **Practical Application**: Real-world scenarios and use cases
- **Self-Paced Learning**: Materials designed for independent study

## Contributing

When adding new projects or materials:
- Follow the established folder structure
- Include both workflow JSON and explanatory README files
- Ensure workflows are tested and functional
- Provide clear, educational documentation

## File Naming Conventions

- **Workflow files**: Use descriptive names ending in `.json`
- **Documentation**: Use `README.md` for project explanations
- **Course content**: Use descriptive names like `outline.md`

This structure ensures that learners can easily navigate between theoretical concepts and practical implementations, creating a comprehensive learning experience for n8n automation.
