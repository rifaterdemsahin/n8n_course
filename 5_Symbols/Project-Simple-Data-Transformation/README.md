# Set Node Workflow

This n8n workflow demonstrates the fundamental concepts of data manipulation using the **Set** node, which is one of the most commonly used nodes in n8n workflows.

## What This Workflow Does

This workflow showcases:

1. **Data Creation and Modification**: Using the Set node to create and modify data
2. **Simple Expressions**: Demonstrating how to use n8n expressions to combine data
3. **Data Flow**: Showing how data passes from one node to another

## Workflow Components

### Nodes in the Workflow

1. **Sticky Note** - Contains documentation explaining the workflow's purpose
2. **Start** - The trigger node that initiates the workflow
3. **Create & Modify Data** (Set node) - The main node that demonstrates data manipulation
4. **View Output** (No Operation node) - A placeholder to view the final output

### Workflow Flow Diagram

```mermaid
graph TD
    A[Sticky Note<br/>Documentation] --> B[Start<br/>Manual Trigger]
    B --> C[Create & Modify Data<br/>Set Node]
    C --> D[View Output<br/>No Operation Node]
    
    C --> E[Static Data Assignment]
    C --> F[Dynamic Expression]
    
    E --> G["firstName: 'Ada'<br/>lastName: 'Lovelace'<br/>userID: 1815"]
    F --> H["fullName: {{$json.firstName}} {{$json.lastName}}"]
    
    G --> I[Final Data Structure]
    H --> I
    I --> J["{<br/>  firstName: 'Ada',<br/>  lastName: 'Lovelace',<br/>  fullName: 'Ada Lovelace',<br/>  userID: 1815<br/>}"]
    
    style A fill:#e1f5fe
    style B fill:#e8f5e8
    style C fill:#f3e5f5
    style D fill:#fff3e0
    style I fill:#fce4ec
```

### Data Structure

The Set node creates the following data structure:

```json
{
  "firstName": "Ada",
  "lastName": "Lovelace", 
  "fullName": "Ada Lovelace",
  "userID": 1815
}
```

### Key Learning Points

#### 1. Static Data Assignment
- `firstName`: Set to "Ada" (static string)
- `lastName`: Set to "Lovelace" (static string)
- `userID`: Set to 1815 (static number)

#### 2. Dynamic Data with Expressions
- `fullName`: Uses the expression `={{$json.firstName}} {{$json.lastName}}`
  - This combines the firstName and lastName fields from the current item
  - The `{{}}` syntax indicates an n8n expression
  - `$json` refers to the current data item

#### 3. Data Types
- **String values**: firstName, lastName, fullName
- **Number values**: userID

### Data Processing Flow

```mermaid
flowchart TD
    A[Input: Empty or Existing Data] --> B{Set Node Processing}
    
    B --> C[Static Assignment]
    B --> D[Expression Evaluation]
    
    C --> E["firstName = 'Ada'<br/>(String)"]
    C --> F["lastName = 'Lovelace'<br/>(String)"]
    C --> G["userID = 1815<br/>(Number)"]
    
    D --> H["Expression: {{$json.firstName}} {{$json.lastName}}"]
    H --> I[String Concatenation]
    I --> J["fullName = 'Ada Lovelace'<br/>(String)"]
    
    E --> K[Data Object Assembly]
    F --> K
    G --> K
    J --> K
    
    K --> L[Output: Complete Data Structure]
    
    style A fill:#f0f0f0
    style B fill:#e3f2fd
    style C fill:#e8f5e8
    style D fill:#fff3e0
    style K fill:#f3e5f5
    style L fill:#e8f5e8
```

## How to Use This Workflow

1. Import the `set-node-workflow.json` file into your n8n instance
2. The workflow will start with the Start node
3. Data flows through the Set node where it's created and modified
4. The final output can be viewed in the "View Output" node

## Expression Syntax

The workflow demonstrates n8n's expression syntax:
- `{{$json.fieldName}}` - Access a field from the current data item
- `{{$json.firstName}} {{$json.lastName}}` - Concatenate two string fields with a space

This is a foundational workflow that teaches the basics of data manipulation in n8n, making it perfect for beginners learning how to work with the Set node and expressions.
