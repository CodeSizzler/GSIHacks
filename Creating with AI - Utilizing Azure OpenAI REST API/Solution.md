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

The completion response to look for is within choices[].text. Notice that also included in the response is
finish_reason , which in this example is stop. Other possibilities for finish_reason include length , which means
it used up the max_tokens specified in the request, or content_filter, which means the system detected
harmful content was generated from the prompt. If harmful content is included in the prompt, the API request
returns an error.

## Task 2 - Chat completions

Similar to completions, chat/completions generates a completion to your prompt, but works best when that
prompt is a chat exchange.

1. Run the following in Git Bash , be sure to replace the placeholders with the information you noted
earlier.

```Bash
curl YOUR_ENDPOINT_NAME/openai/deployments/YOUR_DEPLOYMENT_NAME/chat/completions?apiversion=2023-03-15-preview \
-H "Content-Type: application/json" \
-H "api-key: YOUR_API_KEY" \
-d '{"messages":[{"role": "system", "content": "You are a helpful assistant, teaching
people about AI."},
{"role": "user", "content": "Does Azure OpenAI support multiple languages?"},
{"role": "assistant", "content": "Yes, Azure OpenAI supports several languages, and can
translate between them."},
{"role": "user", "content": "Do other Azure Cognitive Services support translation too?"}]}'
```

2. The response from the API will be similar to the following JSON:

![image](https://github.com/CodeSizzler/JSNOpenAI/assets/100184267/aab0f111-04e5-4380-98cf-ae3e38e96bb0)


Both completion endpoints allow for specifying other optional input parameters, such as temperature,
max_tokens and more. If you'd like to include any of those parameters in your request, add them to the input
data with the request.

## Task 3 - Embeddings

Embeddings are helpful for specific formats that are easily consumed by machine learning models. To generate
embeddings from the input text, POST a request to the embeddings endpoint. When generating embeddings,
you will need to use a model in Azure OpenAI meant for embeddings.

1. In Azure AI Studio, click Deployments on the left then click + Create new deployment. Enter the
following information then click Create. Be sure to note the name of the deployment, my-embeddingmodel, in Notepad.

- Model: text-embedding-ada-002
- Model version: 2 (Default)
- Deployment name: my-embedding-model

![image](https://github.com/CodeSizzler/JSNOpenAI/assets/100184267/78522a23-3d4d-44bc-be16-6a7762a47a19)


2. Run the following in Git Bash , be sure to replace the placeholders with the information you noted
earlier. This time, for the YOUR_DEPLOYMENT_NAME placeholder, use the deployment created in the
previous step, my-embedding-model.

```Bash 
curl YOUR_ENDPOINT_NAME/openai/deployments/YOUR_DEPLOYMENT_NAME/embeddings?api-version=2022-
12-01 \
-H "Content-Type: application/json" \
-H "api-key: YOUR_API_KEY" \
-d "{\"input\": \"The food was delicious and the waiter...\"}"
```

3. The response from the API will be similar to the following JSON:

![image](https://github.com/CodeSizzler/JSNOpenAI/assets/100184267/d8938c2e-6658-4031-b4bc-88a0e8e6be13)


## Clean up

When you're done with your Azure OpenAI resource, remember to delete the resource in the [Azure portal](https://portal.azure.com/?azure-portal=true).





