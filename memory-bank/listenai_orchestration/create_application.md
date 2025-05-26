# Creating and Understanding an Orchestrated Application on LSPlatform

This document guides you through creating a new cloud-orchestrated application on the ListenAI Platform (LSPlatform) using a template, understanding its default flow, and the initial steps for linking it to a "Product." It consolidates information from [Section 4](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#第四章创建并理解您的第一个端云一体化应用) and parts of [Section 5](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#第五章关联云端应用与硬件设备) of the main [ListenAI Hardware Orchestration Tutorial](../ListenAI_Hardware_Orchestration_Tutorial_CN.md).

## I. Creating an Application from a Template

This process leverages pre-built templates for rapid application setup. The primary reference is [Tutorial Section 4.1](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#41-基于模板创建应用) and the ListenAI document [《接入云端可编排应用》 - 创建新应用](https://docs2.listenai.com/x/RtdU8yrbO#创建新应用).

1.  **Access LSPlatform & Application Template Center:**
    *   Log in to the [ListenAI Platform (LSPlatform)](https://platform.listenai.com/).
    *   Navigate to the **"应用模板中心" (Application Template Center)**.

2.  **Select the Template:**
    *   In the "应用模板中心," go to the **"定制开发" (Custom Development)** tab.
    *   Find and select the **"大模型套件语音交互与识图模板" (Big Model Kit Voice Interaction & Image Recognition Template)**.
    *   Click the **"添加应用" (Add Application)** button associated with this template.

3.  **Name and Confirm Application Creation:**
    *   A dialog will appear prompting for an application name.
    *   Enter a descriptive name (e.g., "MyDeviceCloudApp_KB_Test").
    *   Click **"确认创建应用" (Confirm Create Application)**.

Your application is now created based on the selected template.

## II. Exploring the Default Orchestrated Flow

Once the application is created, you need to understand its pre-configured visual flow. This is covered in [Tutorial Section 4.2](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#42-理解默认编排流程). The default flow of the "大模型套件语音交互与识图模板" is detailed in [《接入云端可编排应用》 - 创建新应用 (示例工程对应节点)](https://docs2.listenai.com/x/RtdU8yrbO#创建新应用).

1.  **Navigate to Orchestration View:**
    *   From the application list on LSPlatform, select your newly created application.
    *   Click the **"编排应用" (Orchestrate Application)** button to enter the visual orchestration editor.

2.  **Understand the Template's Default Functionality:**
    The "大模型套件语音交互与识图模板" typically includes a sophisticated multi-modal interaction flow:
    *   **Image-to-Text (图生文):** Understands content from images captured by the device.
    *   **Text-to-Image (文生图):** Generates images based on user's voice descriptions.
    *   **Knowledge Base Q&A (知识库问答):** Answers questions based on a configured knowledge base.
    *   **Fallback Chat (兜底闲聊):** Provides general chat responses if no specific intent or knowledge base answer is matched.

3.  **Default Logical Flow Summary:**
    The typical processing logic is as follows:
    1.  **Image-to-Text Priority:** Checks recent conversation history. If an image-related interaction is ongoing, it continues with image understanding and TTS/text response.
    2.  **Intent Recognition ("Drawing"):** If not an image conversation, it uses an LLM to detect if the user's intent is to "draw" (文生图).
    3.  **Text-to-Image Execution:** If "drawing" intent is confirmed, the flow proceeds to generate an image from the user's text, displays it, and provides TTS feedback.
    4.  **Knowledge Base Retrieval:** If the intent is not "drawing," the system attempts to find relevant information in the configured knowledge base. If found, an LLM formulates an answer from this knowledge.
    5.  **Fallback Chat:** If no specific intent is matched and no knowledge base entries are found, the system defaults to a general LLM-based chat response.

4.  **Key Node Types in the Default Flow:**
    *   **Image Understanding/Vision Model Node:** Processes image data.
    *   **Text Generation/LLM Node:** Handles NLU, Q&A, and text generation.
    *   **Knowledge Point Retrieval Node:** Queries the knowledge base.
    *   **TTS Streaming Node:** Converts text to speech.
    *   **Device Input/Output Nodes:** Manages interaction with the hardware (mic, camera, screen, speaker).

## III. Initial Steps for Linking Application to a "Product"

For the orchestrated application to interact with a physical device, it must be associated with a "Product" on LSPlatform. This is a precursor to full device setup.

1.  **Create a "Product" (if not already done):**
    *   Navigate to **"产品管理" (Product Management)** on LSPlatform.
    *   Click **"新建产品" (New Product)** and provide a name.
    *   **Reference:** [Tutorial Section 5.1](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#51-在lsplatform创建产品), [《接入云端可编排应用》 - 新建产品](https://docs2.listenai.com/x/RtdU8yrbO#h-1-新建产品).

2.  **Configure the "Product" to Use Your Application:**
    *   In "产品管理," select your "Product."
    *   Go to its application configuration settings.
    *   Select/check the orchestrated application you created in Step I of this guide.
    *   Save the configuration.
    *   **Reference:** [Tutorial Section 5.2](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#52-为产品配置应用), [《接入云端可编排应用》 - 配置应用](https://docs2.listenai.com/x/RtdU8yrbO#h-2-配置应用).

After these steps, your cloud application is created and linked to a product. The next major phase is to fully set up and provision your physical device to connect to this product and, by extension, use this orchestrated application. Refer to `setup_device.md` for detailed device provisioning steps.
