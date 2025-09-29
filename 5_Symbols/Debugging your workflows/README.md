# Debugging Your Workflows

## See What Happens Behind the Scenes

Debugging is a crucial skill when working with n8n workflows. Understanding what happens behind the scenes helps you identify issues, optimize performance, and ensure your workflows run as expected.

### Key Debugging Concepts

#### 1. **Execution Flow**
- Each workflow execution creates a unique execution ID
- Nodes process data sequentially (unless using parallel processing)
- Data flows from one node to the next through connections
- Each node can receive input and produce output

#### 2. **Data Inspection**
- **Input Data**: What each node receives from previous nodes
- **Output Data**: What each node produces and passes to next nodes
- **Error Data**: Information about failures and exceptions
- **Execution Logs**: Detailed logs of what happened during execution

#### 3. **Common Debugging Techniques**

##### **Using the Set Node for Debugging**
The Set node is invaluable for debugging because it allows you to:
- **Inspect data**: See exactly what data is flowing through your workflow
- **Add debugging information**: Insert timestamps, execution IDs, or custom markers
- **Transform data for inspection**: Format data in a readable way
- **Create test data**: Generate sample data for testing

##### **Using the Do Nothing Node**
The Do Nothing node is perfect for:
- **Breaking execution flow**: Pause execution to inspect data
- **Testing specific parts**: Isolate sections of your workflow
- **Adding manual checkpoints**: Force manual intervention when needed
- **Creating conditional stops**: Stop execution based on certain conditions

### Debugging Workflow Patterns

#### **Pattern 1: Data Inspection**
```
Start → Set Node (add debug info) → Your Logic → Set Node (inspect results) → End
```

#### **Pattern 2: Conditional Debugging**
```
Start → IF Node (check condition) → Do Nothing Node (debug point) → Continue
```

#### **Pattern 3: Error Handling**
```
Start → Try Logic → Catch Errors → Set Node (log error details) → Handle Error
```

### Best Practices

1. **Use descriptive names** for your debugging nodes
2. **Add timestamps** to track execution timing
3. **Log important variables** at key points in your workflow
4. **Use the Do Nothing node** to create intentional stopping points
5. **Test with small datasets** before running on production data
6. **Use the execution history** to review what happened

### Debugging Tools in n8n

- **Execution History**: View past executions and their results
- **Node Data Viewer**: Inspect input/output data for each node
- **Execution Logs**: Detailed logs of what happened during execution
- **Error Messages**: Clear error descriptions with suggestions
- **Data Preview**: See data structure and content before processing

### Common Issues and Solutions

#### **Data Not Flowing**
- Check node connections
- Verify data structure matches expectations
- Use Set node to inspect data at each step

#### **Unexpected Results**
- Add debugging Set nodes to see intermediate results
- Check data transformations
- Verify conditional logic

#### **Performance Issues**
- Use Do Nothing nodes to isolate performance bottlenecks
- Add timing information with Set nodes
- Check for unnecessary data processing

### Example Debugging Workflow

This section includes practical examples:
- **set-and-edit-node-workflow.json**: Demonstrates using Set nodes for debugging
- **do-nothing-node-workflow.json**: Shows how to use Do Nothing nodes effectively

### Next Steps

1. Import the example workflows
2. Run them to see debugging in action
3. Modify the examples to fit your use cases
4. Practice adding debugging nodes to your own workflows

Remember: Debugging is not just about fixing errors—it's about understanding your data flow and ensuring your workflows work reliably in all scenarios.
