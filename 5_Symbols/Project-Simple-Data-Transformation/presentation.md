---
marp: true
theme: default
---

# Set Node Workflow

---

## What This Workflow Does

- Demonstrates data manipulation using the **Set** node.
- Showcases:
  - Data Creation and Modification
  - Simple Expressions
  - Data Flow

---

## Workflow Components

- **Nodes**:
  - Sticky Note (Documentation)
  - Start (Trigger)
  - Create & Modify Data (Set node)
  - View Output (No Operation node)

---

## Data Structure

The Set node creates the following data structure:

```json
{
  "firstName": "Ada",
  "lastName": "Lovelace",
  "fullName": "Ada Lovelace",
  "userID": 1815
}
```

---

## Key Learning Points

- **Static Data Assignment**:
  - `firstName`: "Ada"
  - `lastName`: "Lovelace"
  - `userID`: 1815
- **Dynamic Data with Expressions**:
  - `fullName`: `={{$json.firstName}} {{$json.lastName}}`

---

## How to Use This Workflow

1.  Import the `set-node-workflow.json` file into your n8n instance.
2.  The workflow will start with the Start node.
3.  Data flows through the Set node where it's created and modified.
4.  The final output can be viewed in the "View Output" node.

---

## Expression Syntax

- `{{$json.fieldName}}`: Access a field from the current data item.
- `{{$json.firstName}} {{$json.lastName}}`: Concatenate two string fields with a space.