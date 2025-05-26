# Setting Up the ListenAI Big Model Development Kit for LSPlatform Orchestration

This document provides a comprehensive step-by-step guide for setting up and provisioning the ListenAI Big Model Development Kit (e.g., CSK6-MIX) for use with the ListenAI Cloud Platform (LSPlatform) orchestration features. It consolidates information from the main [ListenAI Hardware Orchestration Tutorial](../ListenAI_Hardware_Orchestration_Tutorial_CN.md).

## I. Initial Hardware and Software Prerequisites

These steps are primarily detailed in [Section 3 of the main tutorial](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#前提准备与环境设置).

### 1. Hardware Setup:

*   **Device:** ListenAI Big Model Development Kit (CSK6-MIX).
*   **Power:** Connect at least one USB port for power (5V/1A minimum, 5V/2A recommended). Use a separate power adapter if PC USB ports provide insufficient power.
*   **Camera:** Ensure the camera module is correctly installed.
*   **References:**
    *   [Tutorial - Section 3.1](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#1-硬件准备-hardware)
    *   [《视觉语音大模型 AI 开发套件使用说明》](https://docs2.listenai.com/x/nTn9kMMCU)
    *   [《语音交互+识图 功能体验》 - 硬件准备](https://docs2.listenai.com/x/2V18-j2v2#硬件准备)

### 2. Software/Firmware:

*   **Application:** The device must be running the **"语音交互+识图" (Voice Interaction + Image Recognition)** application.
    *   This is typically pre-loaded on the default TF card.
    *   If not, refer to [《语音交互+识图 功能体验》](https://docs2.listenai.com/x/2V18-j2v2) (especially sections "[2] 示例简介" and "[固件下载与烧录]") to load or flash the application.
*   **References:**
    *   [Tutorial - Section 3.2](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#2-软件固件-softwarefirmware)

### 3. Network Configuration:

*   **Connectivity:** The device must be connected to a **2.4GHz Wi-Fi network** with internet access.
*   **Setup Methods:**
    1.  **UI Provisioning:** On the device, go to the home screen, swipe down for the menu, tap "设置" (Settings), then "设备未联网" (Device not networked) or the network configuration option. Select your Wi-Fi, enter the password.
    2.  **QR Code Provisioning:** Use a mobile phone to scan a QR code displayed on the device screen, enter Wi-Fi credentials on the phone-generated webpage, then have the device scan the QR code generated on the phone.
*   **Verification:** A successful connection is usually indicated by a normal Wi-Fi icon and updated time on the device screen.
*   **Troubleshooting Notes:**
    *   Ensure 2.4GHz network.
    *   For iPhone hotspots, enable "Maximize Compatibility."
    *   Router security policies or instability might cause issues; try a mobile hotspot.
*   **References:**
    *   [Tutorial - Section 3.3](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#3-网络配置-network-configuration)
    *   [《语音交互+识图 功能体验》 - 配置网络](https://docs2.listenai.com/x/2V18-j2v2#配置网络)

### 4. LSPlatform Account:

*   **Requirement:** An active [ListenAI Platform (LSPlatform)](https://platform.listenai.com/) account is necessary.
*   **Setup:** If you don't have an account, register at [https://platform.listenai.com/](https://platform.listenai.com/).
*   **API Key:** Ensure you can access/create API Keys (Request Tokens) as needed (e.g., for Knowledge Base services).
*   **References:**
    *   [Tutorial - Section 3.4](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#4-聆思平台账户-lsplatform-account)
    *   [《如何获取API密钥》](https://docs2.listenai.com/x/fZw6AJhn-)

## II. Device Identification and Cloud Registration

These steps involve obtaining the unique device identifier and registering it with your "Product" on LSPlatform. This corresponds to [Tutorial Section 5.3](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#53-获取设备id-chip-id) and [Section 5.4](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#54-添加设备到白名单). The main ListenAI document for these steps is [《接入云端可编排应用》 - 读取设备ID](https://docs2.listenai.com/x/RtdU8yrbO#h-3-读取设备id) and [添加设备白名单](https://docs2.listenai.com/x/RtdU8yrbO#h-4-添加设备白名单).

### 1. Obtain Device ID (Chip ID):

Choose one of the following methods:

*   **Method A: From Device Settings Menu**
    1.  Ensure the "语音交互+识图" application is running.
    2.  On the device's home screen, swipe down to open the menu.
    3.  Tap **设置 (Settings)** icon -> **应用 (Application)**.
    4.  The Device ID will be displayed on the "应用信息查看页" (Application Information Page).

*   **Method B: Via Serial Port Command**
    1.  Connect the device's **DAP_USB** port to your computer.
    2.  Open a serial terminal tool (e.g., [ListenAI Online Serial Terminal](https://tool.listenai.com/serial-term/), PuTTY).
    3.  Configure the connection: Correct COM port, Baud Rate: 115200.
    4.  Send the command: `get chip_id`
    5.  The Device ID will be in the response.

*   **Method C: Using `cskburn desktop` Tool**
    1.  Download and install the [`cskburn desktop` tool](https://docs2.listenai.com/x/oo2_KzYFd).
    2.  Connect the device via USB (usually DAP_USB).
    3.  Run `cskburn desktop`.
    4.  Select the correct serial port from the dropdown.
    5.  Click **获取信息 (Get Information)**. The Device ID will be displayed.

### 2. Add Device ID to Product Whitelist on LSPlatform:

1.  Log in to [LSPlatform](https://platform.listenai.com/).
2.  Navigate to **产品管理 (Product Management)**.
3.  Select the "Product" you intend to use with this device (ensure this "Product" is linked to your desired cloud orchestration application, as per [Tutorial Section 5.1](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#51-在lsplatform创建产品) & [5.2](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#52-为产品配置应用)).
4.  Go to the **设备管理 (Device Management)** page for that "Product".
5.  Import/add the Device ID obtained in the previous step.
*   **Note on Quotas:** LSPlatform may have limits on free test IDs. "产品管理暂不支持删除，如额度已满请在已创建的产品上进行体验。" (Product management currently does not support deletion. If the quota is full, please conduct your experience on an already created product.)

## III. Provisioning Device with Product Credentials

This final step writes the Product ID and Secret ID to the device, enabling it to authenticate with LSPlatform. This corresponds to [Tutorial Section 5.5](../ListenAI_Hardware_Orchestration_Tutorial_CN.md#55-设备端写入产品凭证). The main ListenAI document for these steps is [《接入云端可编排应用》 - 设备端写入配置](https://docs2.listenai.com/x/RtdU8yrbO#h-5-设备端写入配置).

### 1. Obtain Product ID and Secret ID:

*   These are found on LSPlatform, within the **产品信息 (Product Information)** or overview page of your "Product".

### 2. Write Credentials to Device:

Choose one of the following methods:

*   **Method A: Scanning QR Code**
    *   **Firmware Prerequisite:** Device firmware must support this. If not, update using [《应用合集TF卡》](https://docs2.listenai.com/x/oEuqR5JaN).
    1.  On the device (running "语音交互+识图"), swipe down for menu -> **设置 (Settings)** -> **应用 (Application)**.
    2.  Tap **扫码接入 (Scan QR Code to Connect)** button. The camera will activate.
    3.  On LSPlatform, find the product-specific QR code for device provisioning.
    4.  Scan this QR code with the device.
    5.  Verify on the device's application configuration screen that `product_id` and `secret_id` are updated.

*   **Method B: Command Line Interface (CLI)**
    1.  Connect device's **DAP_USB** to PC.
    2.  Open serial terminal (e.g., [ListenAI Online Serial Terminal](https://tool.listenai.com/serial-term/)), connect to the device (Baud: 115200).
    3.  Send commands, replacing placeholders with actual values:
        ```
        set product_id YOUR_PRODUCT_ID_HERE
        set secret_id YOUR_SECRET_ID_HERE
        ```
    4.  **Note for older firmware:** If `set` commands fail, try:
        ```
        aiui set product_id YOUR_PRODUCT_ID_HERE
        aiui set secret_id YOUR_SECRET_ID_HERE
        ```

### 3. Restart Device:

*   After provisioning credentials, **restart the ListenAI Big Model Development Kit** (e.g., toggle power switch or press RST button).

Upon restart, the device should connect to the configured "Product" on LSPlatform and be ready for cloud-orchestrated interactions.
