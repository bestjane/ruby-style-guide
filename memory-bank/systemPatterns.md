# 系统模式：聆思端云一体化流程编排

本文档详细介绍了聆思（ListenAI）端云一体化流程编排的整体系统架构和关键技术模式，旨在为您（Cline）的知识库（Memory Bank）提供更深入的理解。

## 1. 整体系统架构 (Overall System Architecture)

聆思的端云一体化流程编排系统旨在促进聆思硬件（如大模型开发套件）与聆思云平台（LSPlatform）之间的无缝交互。

### 1.1. 端云交互模式 (Device-Cloud Interaction)

此部分描述硬件如何与LSPlatform通信。主要参考文档为[《大模型端云交互链路协议》](https://docs2.listenai.com/x/I7T_gajht)。

*   **通信协议与步骤：**
    1.  **设备授权 (HTTPS)：**
        *   设备首先通过发送 **HTTPS POST** 请求到 `https://api.listenai.com/v1/auth/tokens` 来请求授权。
        *   请求体包含 `productId`（产品ID）、`deviceId`（设备ID）、`curtime`（UTC时间戳）以及一个 `checksum`（由`secretId`、`deviceId`和`curtime`拼接后进行MD5哈希计算得出）。
        *   成功认证后，LSPlatform返回一个JWT `token`及其过期时间。此过程在[教程的凭证写入章节（5.5节）](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#55-设备端写入产品凭证)中有提及，它依赖于这些ID的正确配置。
    2.  **WebSocket会话建立 (WebSocket)：**
        *   获得JWT token后，设备与LSPlatform建立一个 **WebSocket (ws或wss) 连接**。持久连接的典型端点是 `ws[s]://api.listenai.com/v1/interaction`。
        *   JWT token通过WebSocket升级请求的 `Authorization: Bearer <token>` 头部或作为URL参数传递。
    3.  **实时通信 (WebSocket)：**
        *   WebSocket连接建立后，该会话内的所有后续交互（如发送语音/文本数据和接收AI处理结果）都通过此通道进行。
        *   通信涉及发送TEXT消息（JSON格式的命令，用于启动会话、定义数据类型如音频/文本、指定功能如NLU/TTS）和BINARY消息（用于实际的音频数据或其他大型二进制负载）。
        *   云端通过WebSocket消息返回结果（如ASR文本、NLU意图、TTS音频链接/数据）。

*   **认证机制：**
    *   **产品ID与密钥ID (Product ID & Secret ID)：** 设备使用其预置的 `productId` 和 `secretId` 来生成初始HTTPS授权请求所需的 `checksum`。这是云端识别和认证设备所属“产品”上下文的基础（在[教程5.5节](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#55-设备端写入产品凭证)中涵盖）。
    *   **设备白名单：** 授权请求中发送的 `deviceId`（芯片ID）会与LSPlatform上对应“产品”的设备白名单进行核对。只有白名单内的设备才会被授予JWT token（在[教程5.4节](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#54-添加设备到白名单)中涵盖）。
    *   **JWT Token：** 短期有效的JWT token用于认证WebSocket连接及该会话内的后续交互。

### 1.2. LSPlatform核心组件 (LSPlatform Core Components)

LSPlatform提供了一套工具和服务来管理和执行端云一体化流程编排。

*   **应用管理 (Application Management)：**
    *   允许开发者创建、配置和部署流程编排应用。
    *   支持从预定义模板（例如“大模型套件语音交互与识图模板”）创建或可能从头开始创建。
    *   部署过程区分编排环境和生产环境。
    *   （在[教程第四章](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#第四章创建并理解您的第一个端云一体化应用)和[6.4节](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#64-部署变更)中涵盖）。
    *   主要参考文档：[《接入云端可编排应用》](https://docs2.listenai.com/x/RtdU8yrbO) 和 [《在线编排使用说明》](https://docs2.listenai.com/x/ONjKxNdxZ)。

*   **产品管理 (Product Management)：**
    *   支持定义“产品 (Product)”，作为一组设备及其关联云应用的逻辑分组。
    *   每个“产品”拥有唯一的 `productId` 和 `secretId`。
    *   （在[教程5.1节](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#51-在lsplatform创建产品)中涵盖）。

*   **在线编排编辑器 (Orchestration Editor)：**
    *   一个可视化的、基于Web的界面，用于通过连接节点和连线来设计应用逻辑。
    *   允许配置单个节点的属性。
    *   （概念在[教程第二章](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#核心概念节点流程与消息-nodered相似概念解析)中描述，实际操作在[教程4.2节](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#42-理解默认编排流程)和[6.3节](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#63-修改编排流程以集成知识库)中涉及）。
    *   主要参考文档：[《在线编排使用说明》](https://docs2.listenai.com/x/ONjKxNdxZ)。

*   **AI服务集成 (AI Service Integration)：**
    *   各种AI服务（大语言模型、TTS、ASR/NLP、视觉识别、知识库检索）作为功能节点在编排编辑器中提供。
    *   这抽象了直接调用这些服务API的复杂性。开发者可以拖放和配置这些节点。
    *   （示例见[教程4.2节](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#42-理解默认编排流程)和[6.3节](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#63-修改编排流程以集成知识库)）。

*   **设备管理 - 白名单 (Device Management - Whitelisting)：**
    *   管理每个“产品”授权的 `deviceId`（芯片ID）列表。
    *   （在[教程5.4节](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#54-添加设备到白名单)中涵盖）。

## 2. 关键技术模式 (Key Technical Patterns)

聆思端云一体化流程编排系统采用了若干重要的技术模式：

*   **事件驱动架构 (Event-Driven Architecture - EDA)：**
    *   流程由事件启动，这些事件可以来自设备端（如语音命令、按键）或云端（如API调用、定时任务）。这是在[教程第二章](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#核心概念节点流程与消息-nodered相似概念解析)和[第七章](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#第七章聆思流程编排中的nodered核心概念解读-概念映射)中讨论的基本概念。

*   **可视化流程编程 (Visual Flow-Based Programming)：**
    *   通过可视化连接预定义或可配置的节点来设计复杂的应用逻辑，抽象了大部分底层代码。这是在线编排编辑器的核心范式，如[教程第二章](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#核心概念节点流程与消息-nodered相似概念解析)和[第七章](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#第七章聆思流程编排中的nodered核心概念解读-概念映射)所述，并在[《在线编排使用说明》](https://docs2.listenai.com/x/ONjKxNdxZ)中详细说明。

*   **云端卸载处理 (Cloud-Offloaded Processing)：**
    *   计算密集型的AI任务（如LLM推理、复杂NLU、知识库检索、图像生成）在云端的LSPlatform节点中执行。设备处理输入/输出和较简单的任务，将数据发送到云端并接收处理结果。这在默认模板流程中很明显（[教程4.2节](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#42-理解默认编排流程)）。

*   **基于模板的应用创建 (Template-Based Application Creation)：**
    *   LSPlatform提供预构建的应用模板（例如“大模型套件语音交互与识图模板”），为常见用例提供快速启动方案。开发者随后可以自定义这些模板。（在[教程4.1节](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#41-基于模板创建应用)中涵盖，并参考[《接入云端可编排应用》 - 创建新应用](https://docs2.listenai.com/x/RtdU8yrbO#创建新应用)）。

*   **知识库集成模式 (Knowledge Base Integration)：**
    *   一种针对特定领域问答的特定模式，涉及在LSPlatform上创建知识库，并在流程中使用“知识点检索”节点来查询它。（在[教程第六章](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#第六章自定义端云一体化流程)中详细介绍，并基于[《接入云端可编排应用》 - 示例-增加知识库检索](https://docs2.listenai.com/x/RtdU8yrbO#示例-增加知识库检索)）。

*   **安全的设备接入与通信 (Secure Device Onboarding and Communication)：**
    *   涉及产品ID/密钥、设备ID白名单以及JWT认证的WebSocket连接的多步骤过程，确保只有授权设备才能与指定的云应用通信。（在[教程第五章](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#第五章关联云端应用与硬件设备)和[《大模型端云交互链路协议》](https://docs2.listenai.com/x/I7T_gajht)中详细说明）。

理解这些模式将帮助您（Cline）解释系统行为，并指导开发者在聆思平台上构建稳健和可扩展的AIoT应用。
