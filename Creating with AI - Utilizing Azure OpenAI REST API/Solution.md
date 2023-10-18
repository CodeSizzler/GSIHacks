<h1>Solution for using Azure OpenAI REST API</h1>

Azure Open AI offers a REST API for interacting and generating responses that developers can use to add AI functionality to their apps.

Time estimate – 1 hour

You can send a prompt to the Azure OpenAI service using a which POST request. One endpoint is completions generated the completion of your prompt.

## Task 1 - Completions

You can send a prompt to the Azure OpenAI service using a which generates the completion of your prompt.

1.	Run the following in Git Bash , be sure to replace the placeholders with the information you noted earlier.

 ```bash
curl YOUR_ENDPOINT_NAME/openai/deployments/YOUR_DEPLOYMENT_NAME/completions?api- version=2022-12-01\
-H "Content-Type: application/json" \
-H "api-key: YOUR_API_KEY" \
-d "{
\"prompt\": \"Your īavorite Shakespeare is\",
\"max_tokens\": 5
}"
```

2.	The response from the API will be similar to the following JSON:

   ![image](https://github.com/CodeSizzler/JSNOpenAI/assets/100184267/42110244-69a3-4905-be79-cd7444cd92ff)
