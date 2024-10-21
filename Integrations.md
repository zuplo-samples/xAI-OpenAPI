# Integrations

This page contains information about how to integrate the xAI APIs into your application using REST, gRPC or our Python SDK.

Our API is also fully compatible with OpenAI and Anthropic SDKs for easy migration.

## OpenAI SDK

The xAI API offers compatibility with the OpenAI SDKs to support developers and their apps with minimal changes. Once you update the base URL, you can start using the SDKs to make calls to your favorite Grok models with your xAI API key.

### JavaScript

You can import the OpenAI client from 
`openai`
 into your Javascript application and change the base URL and API key.

```javascript


import OpenAI from "openai";
const openai = new OpenAI({
  apiKey: "<api key>",
  baseURL: "https://api.x.ai/v1",
});

const completion = await openai.chat.completions.create({
  model: "grok-2-mini",
  messages: [
    { role: "system", content: "You are Grok, a chatbot inspired by the Hitchhiker's Guide to the Galaxy." },
    {
      role: "user",
      content: "What is the meaning of life, the universe, and everything?",
    },
  ],
});

console.log(completion.choices[0].message);
```

### Python

You can use the 
`openai`
 library to interact with the Grok API in your python program.

```python


import os
from openai import OpenAI

XAI_API_KEY = os.getenv("XAI_API_KEY")
client = OpenAI(
    api_key=XAI_API_KEY,
    base_url="https://api.x.ai/v1",
)

completion = client.chat.completions.create(
    model="grok-2-mini",
    messages=[
        {"role": "system", "content": "You are Grok, a chatbot inspired by the Hitchhikers Guide to the Galaxy."},
        {"role": "user", "content": "What is the meaning of life, the universe, and everything?"},
    ],
)

print(completion.choices[0].message)
```

## Anthropic SDK

xAI SDKs are also fully compatible with the Anthropic SDKs. This allows developers to easily integrate xAI's models into their existing applications. You just need to update the base URL, API key and model name. Below, you can find examples of how to use your xAI API Keys with the Anthropic SDKs.

### JavaScript

You can import the Anthropic SDK from 
`@anthropic-ai/sdk`
 and use it to create a client instance with your xAI API Key.

```javascript


import Anthropic from "@anthropic-ai/sdk";

const anthropic = new Anthropic({
  apiKey: "<api key>",
  baseURL: "https://api.x.ai/",
});

const msg = await anthropic.messages.create({
  model: "grok-2-mini",
  max_tokens: 128,
  system:
    "You are Grok, a chatbot inspired by the Hitchhiker's Guide to the Galaxy.",
  messages: [
    {
      role: "user",
      content: "What is the meaning of life, the universe, and everything?",
    },
  ],
});

console.log(msg);
```

### Python

Likewise, in Python, you can use the 
`Anthropic`
 class to create a client and send a message to the Grok model:

```python


import os
from anthropic import Anthropic

XAI_API_KEY = os.getenv("XAI_API_KEY")
client = Anthropic(
    api_key=XAI_API_KEY,
    base_url="https://api.x.ai",
)
message = client.messages.create(
    model="grok-2-mini",
    max_tokens=128,
    system="You are Grok, a chatbot inspired by the Hitchhiker's Guide to the Galaxy.",
    messages=[
        {
            "role": "user",
            "content": "What is the meaning of life, the universe, and everything?",
        },
    ],
)
print(message.content)
```
