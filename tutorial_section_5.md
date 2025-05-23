# Building a Simple Application: A Step-by-Step Example

With an understanding of the orchestration interface, let's build a basic application. This example will demonstrate how to take user input, process it with a predefined prompt, query the "星火大模型" (Spark Big Model), and then conclude the process, implicitly returning the model's output.

This application will use four fundamental nodes:

1.  **对话入口 (Dialogue Input):** This node serves as the starting point for user interaction, receiving the input query.
2.  **提示词 (Prompt):** This node allows you to define a template or a specific instruction set that will be combined with the user's input to guide the language model.
3.  **星火大模型 (Spark Big Model):** This is the core LLM node that processes the combined input (prompt + user query) and generates a response.
4.  **流程结束 (Process End):** This node signifies the completion of the orchestrated flow.

Here’s how to assemble this application:

## Step 1: Drag and Drop Nodes

1.  **Access the Node Bar:** Locate the "节点栏" (Node Bar) in the orchestration interface.
2.  **Select and Drag Nodes:**
    *   Find the "对话入口" (Dialogue Input) node and drag it into the "编排区" (Orchestration Area).
    *   Next, find the "提示词" (Prompt) node and drag it into the Orchestration Area.
    *   Then, find the "星火大模型" (Spark Big Model) node and drag it into the Orchestration Area.
    *   Finally, find the "流程结束" (Process End) node and drag it into the Orchestration Area.

    Arrange them in a logical sequence to make the connection process easier (e.g., from left to right or top to bottom, in the order listed above).

## Step 2: Connect the Nodes

Nodes in the Orchestration Area have connection points (often represented as small circles or dots on their borders). To create a flow, you'll connect these points.

1.  **Connect Dialogue Input to Prompt:**
    *   Click on the output connection point of the "对话入口" (Dialogue Input) node.
    *   Drag a line to the input connection point of the "提示词" (Prompt) node and release.

2.  **Connect Prompt to Spark Big Model:**
    *   Click on the output connection point of the "提示词" (Prompt) node.
    *   Drag a line to the input connection point of the "星火大模型" (Spark Big Model) node and release.

3.  **Connect Spark Big Model to Process End:**
    *   Click on the output connection point of the "星火大模型" (Spark Big Model) node.
    *   Drag a line to the input connection point of the "流程结束" (Process End) node and release.

After connecting the nodes, your application flow should look like this:

`Dialogue Input` -> `Prompt` -> `Spark Big Model` -> `Process End`

*(The ListenAI documentation includes an image here ("按照下图连接节点" - connect the nodes according to the diagram below) showing the visual representation of these four nodes connected in sequence in the Orchestration Area. Refer to the original documentation for this visual aid.)*

This simple arrangement forms the backbone of many LLM applications. The user's query flows through the "Dialogue Input", is structured by the "Prompt", processed by the "Spark Big Model", and then the process concludes. The actual output to the user would typically be managed by how the "Dialogue Input" node and the platform handle the result from the "Spark Big Model" upon "Process End". The next section will cover configuring these nodes.
