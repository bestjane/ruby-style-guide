# Configuring Nodes

Once you have placed and connected your nodes in the Orchestration Area, the next step is to configure their specific properties. This allows you to customize the behavior of each node to fit your application's requirements.

Generally, you can configure a node by **double-clicking** it in the Orchestration Area. This will open a configuration page or panel, often in the Auxiliary Bar, where you can adjust its settings.

Let's look at how to configure the "提示词" (Prompt) and "星火大模型" (Spark Big Model) nodes from our simple application example:

## Configuring the "提示词" (Prompt) Node

The "提示词" (Prompt) node is crucial for shaping the input that goes into the language model.

1.  **Access Configuration:** Double-click the "提示词" (Prompt) node in your Orchestration Area. This will open its configuration settings.
2.  **Write Prompt Template:** In the configuration panel, you will find an area to write or input your prompt template. This template defines the structure of the query sent to the LLM.
3.  **Using `{{content}}`:** A key part of the prompt template is the placeholder `{{content}}`. This exact syntax is used to mark where the user's input (received from the "对话入口" (Dialogue Input) node) will be inserted into your template. For example, if your template is "Translate the following text to French: {{content}}", the text entered by the user will replace `{{content}}`.

    *(The ListenAI documentation includes an image here showing the configuration page for the Prompt node, with an example of a prompt template being written, highlighting the use of `{{content}}`.)*

## Configuring the "星火大模型" (Spark Big Model) Node

The "星火大模型" (Spark Big Model) node has several parameters that allow you to control the behavior of the language model's response generation.

1.  **Access Configuration:** Double-click the "星火大模型" (Spark Big Model) node in your Orchestration Area to open its configuration settings.
2.  **Adjust Model Parameters:** You can adjust the model's default parameters based on your product needs. The available parameters are:

    *   **`tokens最大值` (Max Tokens):**
        *   **Description:** Defines the maximum length of the generated answer in terms of tokens.
        *   **Type:** Integer
        *   **Default:** 1024
        *   **Range:** Minimum 1, Maximum 4096
        *   **Required:** No

    *   **`temperature`:**
        *   **Description:** This is the nucleus sampling threshold. A lower value (e.g., 0.1) makes the output more deterministic and focused, while a higher value (e.g., 1.0) makes it more random and creative.
        *   **Type:** Float
        *   **Default:** 0.1
        *   **Range:** Minimum 0.1, Maximum 1.0
        *   **Required:** No

    *   **`top_k`:**
        *   **Description:** Instructs the model to select the next token from the `k` most probable tokens. It's a method for random selection, but not uniformly random across all tokens, only among the top k.
        *   **Type:** Integer
        *   **Default:** 4
        *   **Range:** Minimum 1, Maximum 6
        *   **Required:** No

    *   **`流式返回` (Streaming Output):**
        *   **Description:** Determines if the output should be delivered as a stream (i.e., token by token as it's generated) or as a complete block once finished.
        *   **Type:** Boolean
        *   **Default:** False (unchecked)
        *   **Required:** No

    *(The ListenAI documentation includes an image here that displays the configuration page for the Spark Big Model node, showing the fields for `tokens最大值`, `temperature`, `top_k`, and the checkbox for `流式返回`.)*

By carefully setting these parameters for each node, you can fine-tune your application's performance and output to match your desired outcome. Remember that the "对话入口" (Dialogue Input) and "流程结束" (Process End) nodes might also have configurations, though they are simpler in this basic example. Always double-click a node to explore its available settings.
