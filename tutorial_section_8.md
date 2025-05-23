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
