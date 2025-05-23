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
