## 前提准备与环境设置

在开始本端云一体化流程编排教程之前，请确保您已完成以下准备工作。这些是顺利进行后续步骤的基础。

### 1. 硬件准备 (Hardware)

*   **聆思大模型开发套件 (ListenAI Big Model Development Kit):**
    您需要拥有一台聆思大模型开发套件 (CSK6-MIX)。本教程中的所有操作都将围绕此硬件平台展开。请确保您的开发套件能够正常启动和运行。
    *   根据《[视觉语音大模型 AI 开发套件使用说明](https://docs2.listenai.com/x/nTn9kMMCU)》中的“[6] 硬件准备](https://docs2.listenai.com/x/2V18-j2v2#硬件准备)”部分，确保至少连接任一USB口进行供电，并建议将摄像头妥善安装。

### 2. 软件/固件 (Software/Firmware)

*   **运行“语音交互+识图”应用:**
    您的开发套件应预装或已烧录并运行“语音交互+识图” (Voice Interaction + Image Recognition) 应用程序。这是我们进行端云一体化编排的基础应用。
    *   通常，开发套件出厂时默认的TF卡中已包含此应用。您可以直接在应用列表中找到并加载它。
    *   如果您的TF卡中没有此应用，或者您烧录了其他固件，请参照《[语音交互+识图 功能体验](https://docs2.listenai.com/x/2V18-j2v2)》文档中的说明（特别是“[2] 示例简介](https://docs2.listenai.com/x/2V18-j2v2#示例简介)”和可能的“[固件下载与烧录](https://docs2.listenai.com/x/UzjbjIAxw)”部分）来获取和运行此应用。
    *   成功运行后，设备界面应如《[语音交互+识图 功能体验](https://docs2.listenai.com/x/2V18-j2v2)》中“[6] 硬件准备](https://docs2.listenai.com/x/2V18-j2v2#硬件准备)”部分所示的待机界面。

### 3. 网络配置 (Network Configuration)

*   **开发套件联网:**
    为了实现端云一体化编排和与云端AI服务的通信，您的开发套件必须成功连接到互联网（支持2.4G Wi-Fi）。
    *   请严格按照《[语音交互+识图 功能体验](https://docs2.listenai.com/x/2V18-j2v2)》文档中详细的“[8] 配置网络](https://docs2.listenai.com/x/2V18-j2v2#配置网络)”步骤来为您的设备配置Wi-Fi网络。该部分提供了UI配网和二维码配网两种方式。
    *   成功联网后，设备待机界面的Wi-Fi图标应显示正常，并且时间会更新为北京时间。

### 4. 聆思平台账户 (LSPlatform Account)

*   **注册并登录聆思平台:**
    您需要在聆思云平台 (LSPlatform) 上拥有一个有效账户。后续的流程编排、应用管理、API调用等都将在该平台上进行。
    *   如果这是您首次使用聆思平台，您需要先[注册账户](https://platform.listenai.com/)。
    *   关于账户注册、登录以及获取API密钥（Request Token）的详细步骤，您可以参考我们先前的《聆思平台在线流程编排上手教程 (从0到1)》中的“Getting Started: Account and Setup”部分（即 `tutorial_section_2.md` 的内容），或查阅聆思官方提供的其他入门文档。
    *   确保您能够成功登录 [聆思平台 (LSPlatform)](https://platform.listenai.com/)。

完成以上所有准备工作后，您就可以开始学习如何在聆思平台上进行端云一体化的流程编排了。
