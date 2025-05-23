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
