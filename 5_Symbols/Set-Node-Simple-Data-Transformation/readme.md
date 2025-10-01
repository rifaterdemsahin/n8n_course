Of course. Here is the n8n workflow JSON and a corresponding README file that explains the concepts of creating and modifying data, using simple expressions, and passing data between nodes.

-----

## n8n Workflow JSON

Here is the JSON code for the workflow. Copy this code and paste it into your n8n canvas to import it.

```json
{
  "name": "Simple Data Transformation",
  "nodes": [
    {
      "parameters": {},
      "id": "21d15442-8302-4043-8551-700146f499ff",
      "name": "Start",
      "type": "n8n-nodes-base.start",
      "typeVersion": 1,
      "position": [
        240,
        300
      ]
    },
    {
      "parameters": {
        "values": {
          "string": [
            {
              "name": "firstName",
              "value": "Jane"
            },
            {
              "name": "lastName",
              "value": "Doe"
            }
          ]
        },
        "options": {}
      },
      "id": "e2e8e3c4-f2a8-4228-9ec1-11d29505c6d3",
      "name": "1. Create Data",
      "type": "n8n-nodes-base.set",
      "typeVersion": 2,
      "position": [
        460,
        300
      ],
      "notes": "This \"Set\" node creates two new data fields: 'firstName' and 'lastName'."
    },
    {
      "parameters": {
        "values": {
          "string": [
            {
              "name": "fullName",
              "value": "={{ $json.firstName }} {{ $json.lastName }}"
            }
          ]
        },
        "options": {
          "keepOnlySet": false
        }
      },
      "id": "6732e796-03f1-4fd3-8968-07e54f9a7217",
      "name": "2. Modify with Expression",
      "type": "n8n-nodes-base.set",
      "typeVersion": 2,
      "position": [
        680,
        300
      ],
      "notes": "This node uses a simple expression to combine the data from the previous node into a new 'fullName' field."
    }
  ],
  "connections": {
    "Start": {
      "main": [
        [
          {
            "node": "1. Create Data",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "1. Create Data": {
      "main": [
        [
          {
            "node": "2. Modify with Expression",
            "type": "main",
            "index": 0
          }
        ]
      ]
    }
  },
  "settings": {
    "executionOrder": "v1"
  },
  "staticData": null,
  "pinData": {},
  "versionId": "f7895e72-237c-4034-8c85-2e68407cd294",
  "triggerCount": 0,
  "tags": []
}
```

-----

## README.md

# n8n Project: Simple Data Transformation ⚙️

This workflow is a simple, hands-on demonstration of the core concepts mentioned in Lecture 7. It shows you how to create data, pass it to another node, and then modify it using a simple expression.

### 1\. Adding a "Set" Node to Create and Modify Data

The **Set node** is a fundamental tool in n8n for manipulating data. This workflow uses two Set nodes to show its versatility.

  * **Node 1: `Create Data`**
    This first Set node's job is to **create** brand new data from scratch. It is configured to produce two key-value pairs:

      * `firstName`: "Jane"
      * `lastName`: "Doe"
        After this node runs, the data flowing out of it will look like this:

    <!-- end list -->

    ```json
    {
      "firstName": "Jane",
      "lastName": "Doe"
    }
    ```

  * **Node 2: `Modify with Expression`**
    This second Set node's job is to **modify** the incoming data. It takes the data from the previous node and adds a new field called `fullName` without deleting the original fields.

### 2\. Introducing Simple Expressions

Expressions are how you make your workflows dynamic. They allow one node to access and use data from a previous node. 🧠

In the `Modify with Expression` node, we use the following expression to define the value of our new `fullName` field:

`={{ $json.firstName }} {{ $json.lastName }}`

Let's break it down:

  * `{{ ... }}`: This tells n8n that the content inside is an expression to be evaluated, not just plain text.
  * `$json.firstName`: This is a variable that accesses the value of the `firstName` key from the incoming JSON data.
  * `$json.lastName`: Similarly, this accesses the value of the `lastName` key.

The expression simply takes the first name, adds a space, and then adds the last name.

### 3\. Passing Data From One Node to Another

In n8n, data flows from left to right through the connections between nodes. ➡️

1.  The `Start` node runs and passes an empty data object to the `Create Data` node.
2.  The `Create Data` node runs, creating the `firstName` and `lastName` fields.
3.  The output of the `Create Data` node (containing the first and last name) is then passed as the **input** to the `Modify with Expression` node.
4.  Finally, the `Modify with Expression` node runs, uses the data it received, and adds the `fullName` field.

The final output of the entire workflow will be:

```json
{
  "firstName": "Jane",
  "lastName": "Doe",
  "fullName": "Jane Doe"
}
```