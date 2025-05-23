# 聆思平台在线流程编排上手教程 (从0到1)

# Introduction to ListenAI Platform Orchestration

The ListenAI Platform (LSPlatform) is a cloud platform designed for the end-to-end development and deployment of large language model (LLM) applications. It offers a range of functionalities, including knowledge base question answering, low-code application orchestration, request data monitoring, prompt templates, and AI application deployment and sharing.

One of the key features of the ListenAI Platform is its visual process orchestration capability. This provides a highly convenient way to build applications, allowing developers to visually design and arrange the components of their LLM applications online. This visual approach simplifies the development and deployment process for these complex models.

The benefits of using ListenAI's visual process orchestration include:

*   **Ease of Use:** The platform offers a "very convenient application construction method," making it accessible for developers of varying skill levels to build LLM applications.
*   **Speed of Development:** Visual orchestration allows for the rapid "completion of large model application development and deployment."
*   **Web App Sharing:** The platform includes a "Web application sharing function, allowing developers to easily share their Web applications so that others can access and test these applications." This facilitates collaboration and feedback.

# Getting Started: Account and Setup

This section will guide you through creating your ListenAI platform account and setting up the necessary API keys to start building your applications.

## Account Registration

The ListenAI Platform (LSPlatform) is currently in a closed beta phase. To use the platform, you'll need to register for an account and potentially request access.

1.  **Visit the Registration Page:** Go to [https://platform.listenai.com](https://platform.listenai.com) and click on the "注册" (Register) button.
2.  **Complete Registration:** Fill in the required details to create your account.
3.  **Handling "No Permission" Message:**
    *   Since the platform is in closed beta, after logging in, you might encounter a message indicating you don't have permission.
    *   If this happens, click the link provided in the message (often worded as "点击此处链接" - click here link) to fill out an application form.
    *   After submitting the application, you will need to send your name and contact information to ListenAI's business or product personnel. They will then coordinate with the administrator to grant you access.

## Creating an API Key

Once your account has the necessary permissions, you'll need to create an API Key to interact with the platform's services programmatically.

1.  **Log in to the Platform:** Access [https://platform.listenai.com](https://platform.listenai.com) with your credentials.
2.  **Navigate to the Key Module:** On the left-hand side menu, click on the "密钥" (Key) module.
3.  **Create API KEY:** Within the Key module, you will find an option to "创建API KEY" (Create API KEY). Click this to generate your key.
    *   This key will be used for API calls, and you can verify its successful creation and functionality by following the quick start tutorials provided by ListenAI, which usually involve making a test API call and checking for detailed data in the request data module.

## Platform Interface Overview

Upon logging into the ListenAI platform, you will be presented with a user interface designed for managing your LLM applications. The interface includes modules for creating and managing applications, handling API keys, accessing knowledge bases, and orchestrating your AI workflows. The subsequent sections of this tutorial will delve deeper into specific areas, particularly the visual process orchestration interface.

# Creating Your First Application

Now that your account is set up, let's dive into creating your first application using ListenAI's visual process orchestration. This initial step involves navigating to the application module and defining the basic properties of your new application.

Follow these steps:

1.  **Navigate to the Application Module:**
    Once logged into the ListenAI platform, locate the "应用" (Application) module. This is typically found in the main navigation menu.

2.  **Initiate Application Creation:**
    Within the Application module, click on the "创建应用" (Create Application) button. This action will start the process of setting up a new application.
    *(The ListenAI documentation shows an interface where this button is prominently displayed. You would typically see a list of existing applications, if any, and the "Create Application" button allows you to add a new one.)*

3.  **Select Application Type and Name:**
    *   After clicking "创建应用" (Create Application), you will be prompted to choose the type of application. Select "在线编排" (Online Orchestration) as the type. This indicates you will be using the visual tool to build your application's logic.
    *   Next, you need to give your application a unique and descriptive name. Enter a suitable name in the provided field.

    *(The ListenAI documentation includes an image here showing a dialog or form where you select "在线编排" and enter the application name. Refer to the original documentation for the visual context if needed.)*

Once you have selected the type and named your application, it will be created, and you should be able to see it listed in your application module. The next step will be to open this newly created application and start orchestrating its workflow.

# Navigating the Orchestration Interface

Once you have successfully created your application, the next step is to familiarize yourself with the visual orchestration interface. This is where you will design the logic and flow of your LLM application.

## Accessing the Orchestration Interface

1.  **Open Your Application:** In the ListenAI platform's application module, find the application you created in the previous step.
2.  **Enter Orchestration Mode:** Click on your application to open it. You should see an option or button labeled "编排应用" (Orchestrate Application). Click this to enter the visual application orchestration interface.

    *(The ListenAI documentation shows an image at this point, illustrating where to find and click the "编排应用" button after opening an application.)*

## Components of the Online Orchestration Interface

The online orchestration interface is divided into three main sections, designed to help you build and manage your application flow efficiently:

1.  **节点栏 (Node Bar):**
    *   **Purpose:** This area is used for selecting the various nodes you'll need for your application's orchestration. Nodes represent different functions or steps in your process (e.g., input, model interaction, output).
    *   **Location:** Typically, this bar is located on one side of the interface (e.g., the left side).

2.  **编排区 (Orchestration Area):**
    *   **Purpose:** This is the main canvas where you will build your application. You drag nodes from the Node Bar and drop them into this area. You then connect these nodes to define the sequence and logic of your application.
    *   **Location:** This is usually the central part of the interface.

3.  **辅助栏 (Auxiliary Bar):**
    *   **Purpose:** This section provides contextual information and configuration options. It can display:
        *   **Node Information:** Details about a selected node.
        *   **Application Logs:** Logs generated by your application during testing or execution.
        *   **Platform Help:** Access to help documentation or resources.
        *   **Node Configuration:** When a node is selected in the Orchestration Area, its configurable parameters and settings will often appear here, allowing you to customize its behavior.
    *   **Location:** This bar is often located on another side of the interface (e.g., the right side) or as a dynamic panel.

*(The ListenAI documentation includes an image here that provides an overview of the entire orchestration interface, highlighting these three sections: the Node Bar, the Orchestration Area, and the Auxiliary Bar.)*

Understanding these three components is crucial for effectively using the ListenAI platform to visually build and manage your LLM applications. The following sections will guide you on how to use these components to create a simple application.

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

# Deploying Your Application

Once you have completed the orchestration of your nodes—arranging them, connecting them, and configuring their properties—the next crucial step is to deploy your application. Deployment makes your application operational and accessible. The ListenAI platform provides distinct environments for testing and live use.

## Deploying to the Test Environment

The test environment is designed for developers to verify their application's functionality and node configurations without impacting any live users.

1.  **Complete Node Orchestration:** Ensure your application's nodes are fully configured and connected in the visual orchestration interface.
2.  **Deploy to Test:**
    *   Locate the "部署" (Deploy) button. According to the ListenAI documentation, this button is typically found on the **top right corner of the orchestration page**.
    *   Click the "部署" (Deploy) button. This action will deploy your current application configuration to the test environment.

    *(The ListenAI documentation shows an image here illustrating the "部署" (Deploy) button on the orchestration page.)*

    You can use the test environment to thoroughly test your application's logic, different inputs, and node behaviors.

## Deploying to the Production Environment

After you have thoroughly tested your application in the test environment and are confident in its performance, you can deploy it to the production environment. The production environment is where your application will be accessed by end-users or other live systems.

1.  **Return to the ListenAI Platform:** Navigate out of the specific application's orchestration interface and go back to the main ListenAI platform interface (where you see your list of applications, etc.).
2.  **Deploy to Production:**
    *   Find your application in the list.
    *   There will be an option or button labeled "部署生产" (Deploy to Production) associated with your application. Click this button.
    *   This action will take your tested application configuration and deploy it to the live production environment.

    *(The ListenAI documentation includes an image here showing the "部署生产" (Deploy to Production) button, likely on the application management page within the main platform.)*

## Benefit of Separate Environments

The ListenAI platform's provision of separate test and production environments is a key best practice. It allows developers to:
*   **Test Thoroughly:** Experiment with node development, configurations, and new features in the test environment.
*   **Maintain Stability:** Ensure that the live application in the production environment remains stable and unaffected by ongoing development and testing activities. This prevents accidental disruptions to users.

With your application deployed, the next step is often to share it or integrate it, which will be covered next.

# Sharing and Testing Your Application

Once your application has been successfully deployed to the production environment, the ListenAI platform provides a convenient way to share and test it through a web application interface.

## Generating a Web Application Link

After your application is running in the production environment:

1.  **Locate Your Application:** In the main ListenAI platform interface, find your successfully deployed application.
2.  **Generate Share Link:** Click the "分享" (Share) button associated with your application. This action will generate a unique Web application link.

    *(The ListenAI documentation includes an image here showing the "分享" (Share) button, typically found alongside your application in the platform's application management area.)*

3.  **Production Link:** It's important to understand that the Web link generated after deploying to the production environment is the link to the **live, formally running application**. This is the interface that end-users would interact with.

    *(The documentation also shows an example of what this generated Web application link might look like or the interface it leads to.)*

## Accessing and Testing the Web Application

1.  **Use the Link:** Copy the generated Web application link.
2.  **Open in Browser:** Paste this link into a web browser to access your application.
3.  **Test Functionality:** Interact with the web application as an end-user would. Provide inputs and observe the outputs to ensure it behaves as expected according to your orchestration and configurations. This is a crucial step to verify the end-to-end functionality of your deployed LLM application.

## Reminder: Safe Development and Testing

The ListenAI platform's dual-environment system is designed for safe and agile development:

*   **Test Environment for Development:** As highlighted previously, "developers can test and conduct node development in the test environment." This means you can freely experiment, debug, and iterate on your application's design and node configurations.
*   **Production Environment for Stability:** Crucially, activities in the test environment "need not worry about affecting the normal operation of the application in the formal (production) environment." This separation ensures that your live application remains stable and reliable for users while you continue to develop and refine features in a safe sandbox.

By following these steps, you can effectively deploy, share, and test your ListenAI applications, ensuring they are ready for users while maintaining a robust development lifecycle.

# Accessing Your Application via URL (Advanced)

Beyond the user-friendly Web Application interface, ListenAI applications can also be accessed programmatically via direct URL requests. This method is ideal for integrating your LLM application with other services, backend systems, or for use with tools like CURL, Postman, or custom scripts.

## Test and Production Environment URLs

The ListenAI platform provides distinct request URLs for your application depending on whether it's running in the **Test environment** or the **Production environment**. These URLs allow developers to conveniently target the appropriate version of their application for testing or live operations.

*(The ListenAI documentation indicates that the platform provides these specific URLs, likely found within your application's settings or deployment information. You would typically see an image or a section displaying these distinct URLs for test and production.)*

## CURL Request Example

A common way to interact with URL-based APIs is by using CURL. The ListenAI documentation provides a template for making such requests. Below is an example of how to structure a CURL request to your deployed application:

```bash
curl --location 'https://service.listenai.com/{替换为你的应用id}/app-service/chat/completions' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer YOUR_REQUEST_TOKEN' \
--data '{
    "uid": "123",
    "stream": false,
    "messages": [
        {
            "role": "user",
            "content": "请给我国土面积排名前十的国家"
        }
    ]
}'
```

Let's break down the key components of this CURL command:

1.  **Endpoint URL:**
    *   `https://service.listenai.com/{替换为你的应用id}/app-service/chat/completions`
    *   This is the base URL for the chat completions service.
    *   You **must** replace `{替换为你的应用id}` (replace with your application ID) with the actual ID of your ListenAI application. This ID is a unique identifier for your specific application on the platform. *(You would typically find this ID in your application's settings or details page on the ListenAI platform.)*

2.  **Headers:**
    *   `--header 'Content-Type: application/json'`
        *   This header indicates that the data being sent in the request body is in JSON format.
    *   `--header 'Authorization: Bearer YOUR_REQUEST_TOKEN'`
        *   This header is used for authentication.
        *   You **must** replace `YOUR_REQUEST_TOKEN` with your actual API request token (API Key) obtained from the ListenAI platform (as covered in the "Getting Started: Account and Setup" section).

3.  **Data Payload (`--data`):**
    *   This is a JSON object containing the information for your request.
    *   `"uid": "123"`
        *   A user identifier. This can be any string that helps you track or differentiate users or requests.
    *   `"stream": false`
        *   A boolean value. If set to `true`, the response might be streamed. If `false` (as in the example), you'll receive the full response once processed. This corresponds to the "流式返回" (Streaming Output) option in the Spark Big Model node configuration.
    *   `"messages": [...]`
        *   An array of message objects. For a typical user query, this array will contain one object:
            *   `"role": "user"`: Indicates that the content is from the user.
            *   `"content": "请给我国土面积排名前十的国家"`: This is the actual text of the user's query or input. You would replace the example question with your desired input.

## Important Note on Customized Input Node URLs

The documentation points out a crucial detail:
*   "如果在应用编排入口节点改变了对话入口的URL则需根据新URL构建请求体。"
*   This translates to: **If you changed the URL of the "对话入口" (Dialogue Input) node during your application orchestration, you will need to adjust the request URL and potentially the structure of the request body (`--data`) to match your custom configuration.** The default CURL example assumes the standard input node setup.

By understanding and correctly using these URL requests, you can integrate your ListenAI applications into a wider range of automated workflows and services. Remember to always use your specific application ID and API token.

# Managing Your Application

As you develop and iterate on your applications in the ListenAI platform, you may also need to manage them, which includes tasks like updating configurations, monitoring, and sometimes, deletion. This section focuses on how to delete an application you no longer need.

## Deleting an Application

If you need to remove an application from your ListenAI platform account, follow these steps:

1.  **Navigate to Application Settings:**
    *   First, locate the application you wish to delete within the ListenAI platform.
    *   Access its specific settings page. In the ListenAI documentation, this is referred to as the "应用设置" (Application Settings) page. You would typically find a link or button to access these settings from the main application list or dashboard.

2.  **Locate the Delete Button:**
    *   On the "应用设置" (Application Settings) page for the selected application, look for the "删除应用" (Delete Application) button.
    *   According to the documentation, this button is usually found towards the **bottom** of the settings page.

    *(The ListenAI documentation includes an image here illustrating the Application Settings page and highlighting the location of the "删除应用" (Delete Application) button.)*

3.  **Confirm Deletion:**
    *   Click the "删除应用" (Delete Application) button.
    *   As a safety measure to prevent accidental deletions, the system will require you to confirm this action. You will need to **input the name of the application** you are trying to delete into a confirmation field.
    *   Once you have correctly entered the application's name, you can proceed with the deletion.

Deleting an application is typically an irreversible action, so ensure you definitely want to remove it before proceeding. This action will remove the application and its configurations from the platform.

This concludes the basic tutorial on using ListenAI's visual process orchestration. For more advanced features, specific node functionalities, or other aspects of the ListenAI platform, please refer to the official ListenAI documentation.

# Next Steps and Further Learning

Congratulations on completing this introductory tutorial to ListenAI's visual process orchestration! You've learned how to create, configure, deploy, and test a basic LLM application. However, this is just the beginning of what you can achieve with the ListenAI platform.

We encourage you to continue exploring the rich features and capabilities that ListenAI offers. Here are some suggestions for your next steps:

## Dive Deeper into Platform Features:

*   **Explore Knowledge Base Functionality:**
    *   The ListenAI platform allows you to build applications that can answer questions based on your own knowledge bases. This is invaluable for creating specialized, domain-specific AI assistants.
    *   Learn more by exploring the documentation on "[构建自己的知识库问答](https://docs2.listenai.com/x/JdL8tHI4k)" (Building Your Own Knowledge Base Q&A).

*   **Discover Other AI Capabilities:**
    *   ListenAI provides a suite of AI capabilities beyond large language models. Depending on your project needs, you might find these very useful:
        *   **Head & Shoulders/Gesture Recognition ("[头肩&手势识别](https://docs2.listenai.com/x/-N8hFhmGgZn)"):** For applications that need to understand human presence and gestures from images.
        *   **Face Recognition ("[人脸识别](https://docs2.listenai.com/x/L88ow_LYqYU)"):** For applications involving face detection and identification.
    *   Check the main "[AI能力](https://docs2.listenai.com/x/T7H8NYpx58#ai能力)" (AI Capabilities) section on the ListenAI documentation homepage for a broader overview.

*   **Consult Detailed API Documentation:**
    *   For advanced integrations or if you prefer to interact with the platform programmatically, the detailed API documentation is an essential resource.
    *   You can find this at "[API接口](https://api-reference.listenai.com/)" (API Interface), which often includes an online API debugging tool.

## Experiment and Innovate:

*   **Try Different Nodes:** The visual orchestration interface likely offers a variety of nodes beyond the basic ones covered in this tutorial. Drag them into the Orchestration Area, connect them in new ways, and explore their configurations.
*   **Master Prompt Engineering:** The quality of your application's output heavily depends on the prompts you design. Experiment with different phrasings, instructions, and few-shot examples within your "提示词" (Prompt) nodes. The documentation section on "[提示工程](https://docs2.listenai.com/x/7ZMVidLt3)" (Prompt Engineering) can be a good starting point.
*   **Build More Complex Flows:** Try creating applications with multiple branches, conditional logic (if available through specific nodes), or chains of LLM calls.
*   **Integrate with External Tools:** Use the URL access method to connect your ListenAI applications with other software or services you use.

The ListenAI platform is a powerful tool for bringing your AI-driven ideas to life. By continuing to learn and experiment, you'll unlock even more of its potential.

Happy building, and we look forward to seeing what you create!
