# Viewing Your Workflow's Data

This example demonstrates how to understand and navigate JSON data structures in n8n workflows, including the different views available in the output panel.

## Overview

The `data-viewing-workflow.json` contains a comprehensive example that shows:
- Different JSON data structures (flattened, aggregated, nested)
- How to access and transform data
- Navigation techniques for the output panel

## Understanding the JSON Data Structure

### Basic n8n Data Format

Every item in n8n follows this structure:
```json
{
  "json": {
    // Your actual data goes here
  },
  "binary": {
    // Binary data (files, images, etc.) goes here
  }
}
```

### Data Types in JSON

1. **Primitive Types**
   - `string`: Text data (`"John Doe"`)
   - `number`: Numeric data (`30`, `999.99`)
   - `boolean`: True/false values (`true`, `false`)
   - `null`: Empty values

2. **Complex Types**
   - `object`: Key-value pairs (`{"name": "John", "age": 30}`)
   - `array`: Lists of values (`["item1", "item2", "item3"]`)

### Example Data Structures in the Workflow

#### 1. Flattened Structure
```json
{
  "userId": 1,
  "userName": "John Doe",
  "userEmail": "john.doe@example.com",
  "userAge": 30,
  "userCity": "New York",
  "theme": "dark",
  "notifications": true,
  "orderCount": 2,
  "totalSpent": 1139.96,
  "tags": "vip, returning",
  "lastLogin": "2024-03-01T10:30:00Z",
  "isActive": true
}
```

**Characteristics:**
- All data at the same level
- Easy to read and access
- Good for table views
- Simple field references

#### 2. Aggregated Structure
```json
{
  "userId": 1,
  "user": {
    "name": "John Doe",
    "email": "john.doe@example.com",
    "profile": {
      "age": 30,
      "city": "New York",
      "preferences": {
        "theme": "dark",
        "notifications": true
      }
    }
  },
  "summary": {
    "orderCount": 2,
    "totalSpent": 1139.96,
    "averageOrderValue": 569.98,
    "firstOrderDate": "2024-01-15",
    "lastOrderDate": "2024-02-20"
  },
  "metadata": {
    "tags": ["vip", "returning"],
    "lastLogin": "2024-03-01T10:30:00Z",
    "isActive": true
  }
}
```

**Characteristics:**
- Logical grouping of related data
- Nested objects for organization
- Calculated summary fields
- Balanced complexity

#### 3. Nested Structure
```json
{
  "user": {
    "name": "John Doe",
    "email": "john.doe@example.com",
    "profile": {
      "age": 30,
      "city": "New York",
      "preferences": {
        "theme": "dark",
        "notifications": true
      }
    }
  },
  "orderDetails": [
    {
      "orderId": "ORD-001",
      "date": "2024-01-15",
      "total": 1059.97,
      "itemCount": 2,
      "items": ["Laptop (x1) - $999.99", "Mouse (x2) - $29.99"]
    },
    {
      "orderId": "ORD-002",
      "date": "2024-02-20",
      "total": 79.99,
      "itemCount": 1,
      "items": ["Keyboard (x1) - $79.99"]
    }
  ],
  "statistics": {
    "totalOrders": 2,
    "totalItems": 4,
    "totalSpent": 1139.96
  }
}
```

**Characteristics:**
- Deep nesting for complex relationships
- Arrays for multiple items
- Rich detail preservation
- More complex to navigate

## Navigating the Table and JSON Views

### Output Panel Views

When you click on any node in n8n, the output panel at the bottom shows your data in different formats:

#### 1. Table View
- **Purpose**: Shows data in a spreadsheet-like format
- **Best for**: Flattened data structures
- **Navigation**:
  - Scroll horizontally to see all columns
  - Click column headers to sort
  - Use search to filter rows
  - Expand/collapse nested data with arrow icons

#### 2. JSON View
- **Purpose**: Shows raw JSON structure
- **Best for**: Understanding data hierarchy and structure
- **Navigation**:
  - Click arrows to expand/collapse objects and arrays
  - Use Ctrl+F (Cmd+F on Mac) to search within JSON
  - Copy specific values by selecting text

#### 3. Binary View
- **Purpose**: Shows binary data (files, images, etc.)
- **Best for**: Non-text data like images or documents
- **Navigation**:
  - Preview files directly in the browser
  - Download files to your computer
  - View file metadata (size, type, etc.)

### Data Access Patterns

#### Direct Property Access
```javascript
// Access top-level properties
$json.userName
$json.orderCount
$json.totalSpent
```

#### Nested Property Access
```javascript
// Access nested properties using dot notation
$json.user.name
$json.user.profile.age
$json.user.profile.preferences.theme
```

#### Array Access
```javascript
// Access array elements
$json.orders[0]  // First order
$json.orders[0].items[0]  // First item of first order
$json.metadata.tags[0]  // First tag
```

#### Safe Access (Optional Chaining)
```javascript
// Safe access to prevent errors if property doesn't exist
$json.user?.profile?.age
$json.orders?.[0]?.items?.[0]
```

#### Conditional Access
```javascript
// Check if data exists before accessing
{{ $json.orders && $json.orders.length > 0 ? $json.orders[0].total : 0 }}
{{ $json.user?.profile?.preferences?.notifications ? 'Enabled' : 'Disabled' }}
```

## Workflow Nodes Explained

### 1. Manual Trigger
- Starts the workflow execution
- Provides initial input data

### 2. Generate Sample Data (Code Node)
- Creates complex sample data with different structures
- Demonstrates nested objects and arrays
- Shows various data types (strings, numbers, booleans, dates)

### 3. Transform Data Structures (Code Node)
- Converts data into three different formats
- Shows how to flatten, aggregate, and nest data
- Demonstrates data transformation techniques

### 4. Filter Nodes (IF Nodes)
- Separate data by structure type
- Show how to route different data formats
- Demonstrate conditional logic

### 5. Data Access Examples (Code Node)
- Shows different ways to access data
- Demonstrates safe access patterns
- Provides examples of array operations

## Best Practices

### 1. Choose the Right Structure
- **Flattened**: Use for simple data, table views, easy access
- **Aggregated**: Use for balanced complexity, logical grouping
- **Nested**: Use for complex relationships, detailed data

### 2. Consistent Naming
- Use camelCase for property names
- Be descriptive but concise
- Maintain consistent naming patterns

### 3. Safe Data Access
- Always check if properties exist before accessing
- Use optional chaining (`?.`) when available
- Provide default values for missing data

### 4. Performance Considerations
- Avoid overly deep nesting (3-4 levels max)
- Use arrays for multiple similar items
- Consider data size and memory usage

## Tips for Navigation

1. **Use Table View** for:
   - Quick overview of data
   - Comparing multiple records
   - Finding specific values

2. **Use JSON View** for:
   - Understanding data structure
   - Debugging data issues
   - Copying specific values

3. **Use Search** to:
   - Find specific properties or values
   - Navigate large datasets
   - Debug data flow issues

4. **Use Expand/Collapse** to:
   - Focus on relevant data sections
   - Reduce visual clutter
   - Navigate complex structures

## Common Issues and Solutions

### Issue: Cannot access nested property
**Solution**: Check the property path and ensure all parent objects exist
```javascript
// Wrong
$json.user.profile.age  // If profile doesn't exist

// Right
$json.user?.profile?.age  // Safe access
```

### Issue: Array index out of bounds
**Solution**: Check array length before accessing
```javascript
// Wrong
$json.orders[0].total  // If orders array is empty

// Right
{{ $json.orders && $json.orders.length > 0 ? $json.orders[0].total : 0 }}
```

### Issue: Data type mismatch
**Solution**: Convert data types explicitly
```javascript
// Convert string to number
Number($json.age)

// Convert to string
String($json.id)

// Convert to boolean
Boolean($json.isActive)
```

This workflow provides a comprehensive example of working with JSON data in n8n, from basic structures to complex nested data, along with practical navigation techniques for the output panel.
