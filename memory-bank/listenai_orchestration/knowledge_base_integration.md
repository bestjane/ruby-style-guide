# Integrating a Custom Knowledge Base in ListenAI LSPlatform Orchestration

This document provides a step-by-step guide for integrating a custom knowledge base into an existing cloud-orchestrated application on the ListenAI Platform (LSPlatform). This process enables your application, particularly when used with the ListenAI Big Model Development Kit, to answer questions based on your specific domain knowledge. It consolidates information primarily from [Section 6 of the main ListenAI Hardware Orchestration Tutorial](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#第六章自定义端云一体化流程).

The main ListenAI documentation reference for this entire process is [《接入云端可编排应用》 - 示例-增加知识库检索](https://docs2.listenai.com/x/RtdU8yrbO#示例-增加知识库检索).

## I. Creating and Populating the Knowledge Base on LSPlatform

This part corresponds to [Tutorial Section 6.2](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#62-在lsplatform创建知识库).

### 1. API Key Prerequisite:

*   **Crucial Note:** "第一次使用知识库需要创建密钥，请在[密钥页面](https://platform.listenai.com/keys)进行创建对应的API KEY。" (If using the knowledge base for the first time, an API key needs to be created. Please go to the [Key Page](https://platform.listenai.com/keys) to create the corresponding API KEY.)
*   Refer also to [《如何获取API密钥》](https://docs2.listenai.com/x/fZw6AJhn-) for general API key management.

### 2. Steps to Create and Upload:

1.  **Navigate to Knowledge Base Module:**
    *   Log in to [LSPlatform](https://platform.listenai.com/).
    *   From the sidebar, select **"知识库" (Knowledge Base)**.
2.  **Create a New Knowledge Base:** (Ref: [官方文档-新建知识库](https://docs2.listenai.com/x/RtdU8yrbO#新建知识库))
    *   Click **"创建知识库" (Create Knowledge Base)**.
    *   Enter a name for your knowledge base (e.g., "MyProductManual_KB").
    *   Confirm creation.
3.  **Access and Upload Documents:** (Ref: [官方文档-上传文档](https://docs2.listenai.com/x/RtdU8yrbO#上传文档))
    *   Select your newly created knowledge base from the list.
    *   Click **"上传文件" (Upload Files)**.
    *   **Supported Formats:** `txt`, `doc`, `pdf`. Convert other formats if necessary.
    *   Choose your document(s) and upload.
4.  **Set Chunking Strategy:** (Ref: [官方文档-设置分片策略](https://docs2.listenai.com/x/RtdU8yrbO#设置分片策略))
    *   After uploading, you'll be prompted to set a "分片策略" (Chunking Strategy).
    *   The default **"智能分片" (Smart Chunking)** is usually suitable.
    *   Save the strategy.

Your documents are now processed and indexed into the knowledge base.

## II. Modifying the Orchestrated Application Flow

This part corresponds to [Tutorial Section 6.3](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#63-修改编排流程以集成知识库). The main ListenAI documentation reference is [《接入云端可编排应用》 - 在线编排](https://docs2.listenai.com/x/RtdU8yrbO#在线编排).

1.  **Open Your Orchestrated Application:**
    *   On LSPlatform, go to your application list.
    *   Select the application you intend to modify (this should be the one linked to your "Product" and device, typically created from the "大模型套件语音交互与识图模板").
    *   Click **"编排应用" (Orchestrate Application)** to enter the visual editor.

2.  **Locate the "知识点检索" (Knowledge Point Retrieval) Node:**
    *   Within the application's flow diagram, identify the "知识点检索" node. This node is responsible for querying a knowledge base.

3.  **Configure the Node:**
    *   Open the node's configuration panel (usually by double-clicking or selecting it).
    *   Find the option to select a knowledge base (often a dropdown menu).
    *   Choose the knowledge base you created in Part I from the list.
    *   Save the node's configuration.

## III. Deploying the Changes

After modifying the flow, you must deploy the application for the changes to take effect. This is covered in [Tutorial Section 6.4](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#64-部署变更) and at the end of the [《接入云端可编排应用》 - 在线编排](https://docs2.listenai.com/x/RtdU8yrbO#在线编排) section.

1.  **Deploy in Orchestration Editor:**
    *   In the top-right corner of the orchestration editor, click **"部署" (Deploy)**. This saves and deploys the changes to a test/staging environment.

2.  **Deploy to Production:**
    *   Return to the main application list/management page on LSPlatform.
    *   Find your modified application.
    *   Click the **"部署生产" (Deploy to Production)** button. This pushes the changes to the live environment your device uses.

3.  **Restart Device:**
    *   **Crucial Step:** "完成上述部署后，重启设备，此时自定义应用已经完成修改。" (After completing the above deployment, restart the device. At this point, the custom application modification is complete.)
    *   Restart your ListenAI Big Model Development Kit.

## IV. Testing the Knowledge Base Integration

Verify that the integration works as expected. This is covered in [Tutorial Section 6.5](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#65-测试自定义后的流程).

1.  **Interact with Your Device:**
    *   Ensure the device is powered on, connected to the network, and linked to the correct "Product."
    *   Use the normal interaction method (voice wake-up or button press).

2.  **Ask Specific Questions:**
    *   Ask questions whose answers are contained **only** within the documents you uploaded to your custom knowledge base.
    *   Example: If you uploaded an air conditioner manual, ask "How do I clean the air conditioner filter?"

3.  **Evaluate Responses:**
    *   The device should now provide answers based on the content of your custom knowledge base.
    *   These answers should be specific to your documents and distinguishable from general LLM responses or other intents (like image generation).
    *   The ListenAI documentation provides an [example image of a successful knowledge base interaction](https://docs2.listenai.com/x/RtdU8yrbO#示例-增加知识库检索) (look for `73074f126cdb634bc4817e5dcd077b1c.jpg`).

If the responses are not as expected, review all steps: knowledge base creation, document upload, chunking, API key, node configuration in the flow, and deployment, ensuring the device was restarted.
