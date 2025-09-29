# 4_Formula - Formulas, Expressions & Calculations

This folder contains comprehensive guides for n8n expressions, formulas, and calculations. Master these to unlock the full power of n8n's data manipulation capabilities.

## Overview

n8n expressions are powerful tools for data transformation, conditional logic, and dynamic content generation. This folder provides a complete reference for all expression types, syntax, and practical examples.

## Expression Categories

### Basic Expressions
- **String Operations** Concatenation, formatting, and manipulation
- **Mathematical Calculations** Arithmetic, rounding, and number formatting
- **Date and Time** Date parsing, formatting, and calculations
- **Boolean Logic** True/false evaluations and conditional expressions

### Advanced Expressions
- **Array Operations** Filtering, mapping, and reducing arrays
- **Object Manipulation** Property access, merging, and transformation
- **Regular Expressions** Pattern matching and text extraction
- **JSON Operations** Parsing, stringifying, and deep property access

### n8n-Specific Expressions
- **Node References** Accessing data from previous nodes
- **Workflow Context** Global variables and execution data
- **Credential Access** Secure credential retrieval
- **Environment Variables** Configuration value access

## Expression Syntax Reference

### Basic Syntax
```javascript
// String concatenation
{{ $json.firstName + ' ' + $json.lastName }}

// Mathematical operations
{{ $json.price * 1.1 }} // Add 10% tax

// Date formatting
{{ $now.format('YYYY-MM-DD') }}

// Conditional logic
{{ $json.age >= 18 ? 'Adult' : 'Minor' }}
```

### Advanced Syntax
```javascript
// Array filtering
{{ $json.items.filter(item => item.active) }}

// Object property access
{{ $json.user.profile.email }}

// Regular expressions
{{ $json.text.match(/\d{3}-\d{3}-\d{4}/) }}

// JSON manipulation
{{ JSON.parse($json.jsonString).property }}
```

## Common Use Cases

### Data Transformation
- **Format Conversion** Converting between data types
- **Field Mapping** Renaming and restructuring data
- **Value Calculation** Computing derived values
- **Data Validation** Checking data integrity

### Conditional Processing
- **Route Logic** Directing workflow paths based on data
- **Content Generation** Creating dynamic messages and documents
- **Error Handling** Providing fallback values
- **Business Rules** Implementing complex decision logic

### Integration Patterns
- **API Response Processing** Extracting and formatting API data
- **Database Queries** Building dynamic SQL and NoSQL queries
- **File Processing** Parsing and generating file content
- **Notification Content** Creating personalized messages

## Formula Libraries

### String Formulas
- Text cleaning and normalization
- Pattern extraction and replacement
- Case conversion and formatting
- Length validation and truncation

### Mathematical Formulas
- Business calculations (taxes, discounts, margins)
- Statistical operations (averages, totals, percentages)
- Currency conversions and formatting
- Unit conversions and scaling

### Date Formulas
- Relative date calculations (days ago, weeks from now)
- Business day calculations (excluding weekends/holidays)
- Time zone conversions
- Duration calculations

### Data Validation Formulas
- Email format validation
- Phone number formatting
- URL validation and normalization
- Required field checking

## Best Practices

### Performance Optimization
- **Efficient Expressions** Minimizing computational complexity
- **Caching Strategies** Reusing calculated values
- **Error Prevention** Handling edge cases gracefully
- **Resource Management** Avoiding memory-intensive operations

### Security Considerations
- **Input Validation** Sanitizing user inputs
- **Credential Protection** Secure credential handling
- **Data Privacy** Protecting sensitive information
- **Access Control** Limiting expression capabilities

### Maintainability
- **Documentation** Commenting complex expressions
- **Modularity** Breaking complex logic into smaller parts
- **Testing** Validating expressions with sample data
- **Version Control** Tracking expression changes

## Testing and Debugging

### Expression Testing
- **Sample Data Testing** Using realistic test data
- **Edge Case Validation** Testing boundary conditions
- **Error Scenario Testing** Handling invalid inputs
- **Performance Testing** Measuring execution time

### Debugging Techniques
- **Step-by-Step Evaluation** Breaking down complex expressions
- **Console Logging** Outputting intermediate values
- **Error Handling** Graceful failure management
- **Documentation** Recording expression purposes

## Learning Path

### Beginner Level
1. Basic string and number operations
2. Simple conditional logic
3. Date formatting and manipulation
4. Basic node data access

### Intermediate Level
1. Array operations and filtering
2. Object manipulation
3. Regular expressions
4. Complex conditional logic

### Advanced Level
1. Custom function creation
2. Performance optimization
3. Security considerations
4. Integration patterns

## Resources

### Documentation
- n8n Expression Reference
- JavaScript MDN Documentation
- Regular Expression Guides
- Date/Time Libraries

### Tools
- Expression Validators
- Regular Expression Testers
- JSON Validators
- Code Formatters

### Community
- n8n Community Forum
- Expression Sharing Platforms
- Stack Overflow n8n Tag
- GitHub Examples

## Integration with Course

This formula knowledge directly supports:
- **`5_Symbols/`** - Practical projects using expressions
- **`6_Semblance/`** - Visual examples of expression results
- **`7_Testing/`** - Validating expression correctness
- **`1_Real/`** - Achieving key results through expression mastery

Mastering n8n expressions is essential for creating sophisticated, dynamic workflows that can handle complex business logic and data transformations.
