# 当前上下文：聆思平台流程编排知识库 (Memory Bank)

## 当前工作焦点 (Current Work Focus)

当前工作焦点是为聆思平台（LSPlatform）的流程编排功能构建初始阶段的知识库（Memory Bank）。此阶段的目标是创建一套结构化的文档，使您（Cline）能够深入理解并协助开发者有效使用该平台。

## 近期变更 (Recent Changes)

以下关键文档和指南已起草/修正，构成本知识库的初步核心内容：

*   **核心知识库文件：**
    *   `projectbrief.md` (项目简报 - 已更新为中文内容)：定义了本知识库的目标和范围。
    *   `productContext.md` (产品背景 - 已更新为中文内容)：解释了聆思端云一体化流程编排功能的目的、解决的问题及核心工作原理。
    *   `systemPatterns.md` (系统模式 - 已更新为中文内容)：详细描述了整体系统架构和关键技术模式。
    *   `techContext.md` (技术背景 - 已更新为中文内容)：概述了所涉及的关键技术、框架、限制及依赖。
*   **`listenai_orchestration/` 目录下的详细指南：**
    *   `setup_device.md` (设备设置与凭证写入指南)：关于聆思大模型开发套件针对LSPlatform的完整设置流程。
    *   `create_application.md` (应用创建与理解指南)：关于如何基于模板创建应用并理解其默认流程。
    *   `knowledge_base_integration.md` (知识库集成指南)：关于如何集成自定义知识库到应用流程中。
    *   `node_knowledge_retrieval.md` (节点详解：“知识点检索”)：深入介绍“知识点检索”节点。
    *   `node_llm.md` (节点详解：“大模型”)：深入介绍“大模型”/“星火大模型”节点。

## 后续步骤 (Next Steps for Memory Bank population)

知识库的后续填充将包括：

*   添加更多关于其他重要聆思流程编排节点（例如：TTS节点、设备输入/输出节点、具体的逻辑控制节点）的详细“节点详解”文档。
*   记录更高级的流程编排技巧和设计模式。
*   扩充问题排查指南，包含更多具体的问题场景和解决方案。
*   提供更多样化的具体使用案例，以展示平台的广泛能力。
*   （视情况）创建一个与聆思平台流程编排相关的专用术语表。

## 当前决策与考量 (Active Decisions/Considerations)

*   **主要信息来源：** 当前知识库内容主要来源于《聆思端云一体化流程编排上手教程 (大模型硬件开发套件)》（路径 `../ListenAI_Hardware_Orchestration_Tutorial_CN.md`）以及聆思官方文档，包括：
    *   [《接入云端可编排应用》 (RtdU8yrbO)](https://docs2.listenai.com/x/RtdU8yrbO)
    *   [《在线编排使用说明》 (ONjKxNdxZ)](https://docs2.listenai.com/x/ONjKxNdxZ)
    *   [《大模型端云交互链路协议》 (I7T_gajht)](https://docs2.listenai.com/x/I7T_gajht)
    *   以及这些文档链接到的其他相关具体细节文档（如API密钥创建、开发套件设置等）。
*   **信息层级结构：** 详细的流程指南和节点 स्पेसिफिक (specific) 信息被组织在 `listenai_orchestration/` 子目录下，以保持主知识库的清晰结构。

## 重要模式与偏好 (Important Patterns/Preferences for Documentation)

*   **清晰性与结构化：** 所有文档都力求内容清晰、简洁且结构良好，以便于您（Cline）理解和检索信息。
*   **面向AI辅助使用：** 内容编写时已考虑到主要使用者是AI助手（Cline），因此尽可能使用明确无歧义的语言，并提供清晰的上下文。
*   **可追溯性：** 优先链接回原始的官方文档或综合教程 (`../ListenAI_Hardware_Orchestration_Tutorial_CN.md`)，以确保信息可被核实，并在需要时查找更深入的背景信息。
*   **Markdown格式：** 所有文档均采用Markdown格式。
*   **教程内容的语言：** 所参考的核心教程及大部分源文档为中文；本知识库在引用和总结时也主要使用中文，以保持上下文的一致性。
