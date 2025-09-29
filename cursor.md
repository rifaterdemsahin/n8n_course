# n8n Course Project Structure

This project contains educational materials and workflows for learning n8n automation. The structure is organized to provide a comprehensive learning experience with practical examples.

## Project Overview

This is an n8n course project designed to teach automation concepts through hands-on examples and structured learning materials.

## Directory Structure

```
n8n-course/
├── n8n_course/                           # Main course content
│   ├── outline.md                        # Course outline and curriculum
│   └── README.md                         # Course introduction and overview
├── Symbols/                              # Project examples and workflows
│   └── Project - Simple Data Transformation/
│       ├── README.md                     # Detailed explanation of the workflow
│       └── set-node-workflow.json       # n8n workflow file
└── cursor.md                            # This file - project structure guide
```

## How to Use This Project

### 1. Course Materials (`n8n_course/`)
- **`outline.md`**: Contains the complete course curriculum and learning path
- **`README.md`**: Provides course introduction, prerequisites, and getting started guide

### 2. Project Examples (`Symbols/`)
Each project folder contains:
- **Workflow JSON files**: Ready-to-import n8n workflows
- **README.md**: Detailed explanations of what each workflow does and how to use it

#### Current Projects:

##### Project - Simple Data Transformation
- **Purpose**: Teaches fundamental data manipulation using the Set node
- **Files**:
  - `set-node-workflow.json`: Import this into n8n to see the workflow in action
  - `README.md`: Comprehensive guide explaining:
    - What the workflow demonstrates
    - How each node works
    - Key learning concepts
    - Expression syntax examples

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
