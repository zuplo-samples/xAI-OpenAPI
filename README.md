# xAI OpenAPI

OpenAPI file for xAI. Subsequent documentation is directly from the xAI docs (last update Oct 2 2024).
Their latest OpenAPI can be found at: [https://docs.x.ai/openapi.json](https://docs.x.ai/openapi.json)

## Interactive API Docs

You can get live code samples and a full test console using this [Zudoku Sample](https://zudoku.dev/demo?api-url=https://raw.githubusercontent.com/zuplo-samples/xAI-OpenAPI/refs/heads/main/xAI-openapi.json).

## Quickstart
This page is designed to help you get up and running with our API, including setting up your account and documenting the API and its available functionality.

## Creating your account

To use your API, you will first need to create an account. Start by navigating to xAI Console to sign up.

Once you have logged in, you will be guided through an onboarding process to create a team and invite your teammates.

Each team has its own set of users, API keys and billing information. You can create as many teams as you need. Once your team is set up, you will need to add a payment method from the billing page and purchase credits to start using the API.

## Creating an API key

Once you have completed onboarding, you can navigate to the API Keys page to create your first API key.

Choose a name for your API key and select which endpoints and models the key will have access to.

Store your API key in a secure location, and never share it publicly. If you lose your API key, you can delete the previous key and generate a new one from this page.

Once you’ve generated an API key, export it as an environment variable in your terminal.

```bash


export XAI_API_KEY="your_api_key_here"

```

## Making your first request

With your xAI API key exported as an environment variable, you're ready to make your first API request.

Let's test out the API using 
curl
. The command below assumes that you have exported the 
XAI_API_KEY
 as a system environment variable.

```bash


curl https://api.x.ai/v1/chat/completions \\
  -H "Content-Type: application/json" \\
  -H "Authorization: Bearer $XAI_API_KEY" \\
  -d '{
        "messages": [
          {
            "role": "system",
            "content": "You are Grok, a chatbot inspired by the Hitchhikers Guide to the Galaxy."
          },
          {
            "role": "user",
            "content": "What is the meaning of life, the universe, and everything?"
          }
        ],
        "model": "grok-beta",
        "stream": false,
        "temperature": 0
      }'
```

In your application, you can integrate with the xAI API using our REST API, gRPC API, or an SDKs as our API is OpenAI and Anthropic compatible.

## Monitor usage

As you use your API key, you will be charged for the number of tokens used. You can monitor your usage in the xAI console usage page.
