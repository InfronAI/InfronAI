# Welcome to Infron

Infron provides a unified API that gives you access to hundreds of AI models through a single endpoint, while automatically handling fallbacks and selecting the most cost-effective options. Get started with just a few lines of code using your preferred SDK or framework.

The first step to start using Infron is to [create an account](https://app.onerouter.pro/index) and [get your API key](https://app.onerouter.pro/apiKeys).

After that, feel free to explore our API reference for more details. Or to jump start into our first example below.

## Using the OpenAI SDK

```python
from openai import OpenAI

client = OpenAI(
  base_url="https://llm.onerouter.pro/v1",
  api_key="<API_KEY>",
)

completion = client.chat.completions.create(
  model="claude-3-5-sonnet@20240620",
  messages=[
    {
      "role": "user",
      "content": "What is the meaning of life?"
    }
  ]
)

print(completion.choices[0].message.content)
```


```typescript
import OpenAI from 'openai';

const openai = new OpenAI({
  baseURL: 'https://llm.onerouter.pro/v1',
  apiKey: '<API_KEY>',
});

async function main() {
  const completion = await openai.chat.completions.create({
    model: 'claude-3-5-sonnet@20240620',
    messages: [
      {
        role: 'user',
        content: 'What is the meaning of life?',
      },
    ],
  });

  console.log(completion.choices[0].message);
}

main();
```


## Using the Infron API directly


```python
import requests
import json

response = requests.post(
  url="https://llm.onerouter.pro/v1/chat/completions",
  headers={
    "Authorization": "Bearer <API_KEY>",
    "Content-Type": "application/json"
  },
  data=json.dumps({
    "model": "claude-3-5-sonnet@20240620", 
    "messages": [
      {
        "role": "user",
        "content": "What is the meaning of life?"
      }
    ]
  })
)
print(response.json()["choices"][0]["message"]["content"])
```

```typescript
fetch('https://llm.onerouter.pro/v1/chat/completions', {
  method: 'POST',
  headers: {
    Authorization: 'Bearer <API_KEY>',
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    model: 'claude-3-5-sonnet@20240620',
    messages: [
      {
        role: 'user',
        content: 'What is the meaning of life?',
      },
    ],
  }),
});
```


```sh
curl https://llm.onerouter.pro/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $API_KEY" \
  -d '{
  "model": "claude-3-5-sonnet@20240620",
  "messages": [
    {
      "role": "user",
      "content": "What is the meaning of life?"
    }
  ]
}'
```


The API also supports [streaming](https://infronai.gitbook.io/docs/api-reference/llm-model-api/streaming).

## Using third-party SDKs

For information about using third-party SDKs and frameworks with Infron, please see our [frameworks documentation](https://infronai.gitbook.io/docs/frameworks-and-integrations/overview).

## FAQ

### Getting started <a href="#getting-started" id="getting-started"></a>

<details>

<summary><strong>Why should I use Infron AI?</strong></summary>

Infron AI provides a unified API to access all the major LLM models on the market. It also allows users to aggregate their billing in one place and keep track of all of their usage using our analytics.

Infron AI passes through the pricing of the underlying providers, while pooling their uptime, so you get the same pricing you’d get from the provider directly, with a unified API and fallbacks so that you get much better uptime.

</details>

<details>

<summary><strong>What makes Infron AI unique?</strong></summary>

Infron AI stands out as a unified routing layer that connects multiple AI model providers through a single, consistent API. Instead of integrating separately with different LLM or embedding services, developers can use Infron AI to simplify model management, request routing, and version control.&#x20;

Infron AI offers flexible configuration options—such as automatic provider selection, fallback routing, and performance optimization—which help ensure reliability and cost-efficiency. In short, Infron AI makes it easier to build and scale AI applications by abstracting away provider complexity while maintaining full transparency and control.

</details>

<details>

<summary><strong>What's the story behind Infron AI?</strong></summary>

Infron AI was created to solve a growing pain in the AI development world: managing multiple model providers efficiently. As the ecosystem of large language models and embeddings expanded, developers often found themselves juggling different APIs, authentication methods, and data formats for each provider. This added unnecessary friction and slowed down innovation.

Seeing this challenge, the creators of Infron AI envisioned a single, unified routing layer that could abstract away these complexities—allowing developers to focus on what matters most: building great products powered by AI. The idea was to give teams the flexibility to mix and match providers, experiment seamlessly, and improve reliability through smart routing and fallbacks.

From that vision, Infron AI emerged as an infrastructure solution designed to make multi‑provider AI development as simple, scalable, and transparent as possible. It reflects the broader effort to move from fragmented model integrations toward a cohesive, provider‑agnostic AI ecosystem.

</details>

<details>

<summary><strong>Why should a person choose Infron AI over its competitors?</strong></summary>

Infron AI offers a flexible and developer‑friendly way to manage multiple AI model providers through one unified API. Unlike tools that tie you to a single vendor, Infron AI lets you easily switch or combine models from different sources without changing your application code.&#x20;

Infron AI provides built‑in routing logic, fallback mechanisms, and usage tracking so you can optimize cost, latency, and reliability automatically. In addition, its configuration‑based approach and detailed observability tools simplify scaling and debugging. In short, Infron AI helps teams focus on building AI‑powered features rather than maintaining complex provider integrations.

</details>

<details>

<summary><strong>Who are the primary audience of Infron AI?</strong></summary>

The primary audience of Infron AI includes developers, product teams, and organizations building applications that rely on AI models or large language models (LLMs).&#x20;

Infron AI is designed for engineers who need to integrate, manage, and optimize access to multiple AI providers without maintaining separate APIs. Startups, enterprise AI teams, and platform builders can all benefit from its unified routing system—especially those seeking flexibility, scalability, and cost control in multi‑provider environments. In essence, Infron AI serves anyone who wants to simplify AI infrastructure while maintaining high performance and reliability.

</details>

<details>

<summary><strong>How do I get started with Infron AI?</strong></summary>

To get started, create an account and add credits on the [Credits](https://app.onerouter.pro/credits) page. Credits are simply deposits on Infron AI that you use for LLM inference. When you use the API or chat interface, we deduct the request cost from your credits. Each model and provider has a different price per million tokens.

Once you have credits you can create API keys and start using the API. You can read our [quickstart](https://infronai.gitbook.io/docs/overview/readme) guide for code samples and more.

</details>

<details>

<summary><strong>How do I get support?</strong></summary>

The best way to get support is to submit an [issue](https://github.com/TrustAI-laboratory/OneRouter/issues).

</details>

<details>

<summary><strong>How do I get billed for my usage on Infron AI?</strong></summary>

For each model we have the pricing displayed per million tokens. There is usually a different price for prompt and completion tokens. There are also models that charge per request, for images and for reasoning tokens. All of these details will be visible on the [Logs tab](https://app.onerouter.pro/logs).

When you make a request to Infron AI, we receive the total number of tokens processed by the provider. We then calculate the corresponding cost and deduct it from your credits. You can review your complete usage history in the [Activities tab](https://app.onerouter.pro/index).

You can also add the `usage: {include: true}` parameter to your chat request to get the usage information in the response.

We offer different discounts ranging from 20% to 80% based on the pricing of underlying providers.

</details>

### Pricing <a href="#pricing-and-fees" id="pricing-and-fees"></a>

<details>

<summary><strong>What are the prices for using Infron AI?</strong></summary>

Infron AI charges a $0.35 + 5% fee when you purchase credits. We pass through the pricing of the underlying model providers without any markup, so you pay the same rate as you would directly with the provider.

For more details on our model price, please see our [Models tab](https://app.onerouter.pro/models).

For more details about every request cost, please see our [Logs tab](https://app.onerouter.pro/logs).

</details>

<details>

<summary><strong>How is the billing calculated when Prompt Cache is enabled?</strong></summary>

Regardless of whether the cached result is used or a new prompt is processed, billing will follow the Prompt Cache rate as defined in our pricing documentation. This applies to every request, since Prompt Cache is always active in Infron AI.

<figure><img src="https://3822312837-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FZ9C9AjT7j46HAcQrOVWw%2Fuploads%2FvP3ro8XdW4jF9xz2o0F7%2Fimage.png?alt=media&#x26;token=2b42fa86-fd26-488a-8322-6864a9657657" alt=""><figcaption></figcaption></figure>

</details>

### Models and Providers <a href="#models-and-providers" id="models-and-providers"></a>

<details>

<summary><strong>What LLM models does Infron AI support?</strong></summary>

Infron AI provides access to a wide variety of LLM models, including frontier models from major AI labs.&#x20;

For a complete list of models you can visit the [Models tab](https://app.onerouter.pro/models) or fetch the list through the [models api](https://app.onerouter.pro/api/display_models).

</details>

<details>

<summary><strong>How frequently are new models added?</strong></summary>

We work on adding models as quickly as we can. We often have partnerships with the labs releasing models and can release models as soon as they are available.

If there is a model missing that you’d like Infron AI to support, feel free to message us on [issue](https://github.com/TrustAI-laboratory/OneRouter/issues).

</details>

<details>

<summary><strong>I am an inference provider, how can I get listed on Infron AI?</strong></summary>

If you would like to contact us, the best place to reach us is over email.

</details>

<details>

<summary><strong>How does model fallback work if a provider is unavailable?</strong></summary>

If a provider returns an error Infron AI will automatically fall back to the next provider. This happens transparently to the user and allows production apps to be much more resilient.

</details>

### API Technical Specifications <a href="#api-technical-specifications" id="api-technical-specifications"></a>

<details>

<summary><strong>What authentication methods are supported?</strong></summary>

Infron AI uses three authentication methods:

1. API keys (passed as Bearer tokens) for accessing the completions API and other core endpoints

</details>

<details>

<summary><strong>What API endpoints are available?</strong></summary>

Infron AI implements the OpenAI API specification for /completions and /chat/completions endpoints, allowing you to use any model with the same request/response format.&#x20;

Additional endpoints like /api/v1/models are also available. See our [API documentation](https://infronai.gitbook.io/docs/api-reference/llm-model-api/overview) for detailed specifications.

</details>

<details>

<summary><strong>Which are the primary technologies used for building Infron AI?</strong></summary>

Infron AI is typically built using modern, cloud‑native web technologies optimized for performance, scalability, and integration with AI services. At its core, Infron AI relies on:

1. **TypeScript and Node.js** – for the main API logic, routing, and configuration management. These enable a robust developer experience and compatibility with diverse model providers.
2. **Cloud infrastructure (e.g., AWS, GCP, or similar)** – to support distributed routing, load balancing, and secure service deployment across regions.
3. **Database and caching systems** – often using PostgreSQL or similar for persistent data, and Redis or in‑memory stores for high‑speed routing decisions.
4. **API and network layer technologies** – including REST and WebSocket interfaces, authentication systems, and observability tooling to track provider usage and latency.
5. **Integration SDKs and AI provider APIs** – connectors built for leading LLM and AI platforms (such as OpenAI, Anthropic, Google, etc.) to enable seamless model switching.

Together, these technologies provide a flexible foundation that allows Infron AI to route, monitor, and optimize traffic across multiple AI services effectively.

</details>

<details>

<summary><strong>What are the supported formats?</strong></summary>

The API supports text and images. [Images](https://infronai.gitbook.io/docs/features/multimodal-input/images-inputs) can be passed as URLs or base64 encoded images. PDF and other file types are coming soon.

</details>

<details>

<summary><strong>How does streaming work?</strong></summary>

Streaming uses server-sent events (SSE) for real-time token delivery.&#x20;

Set `stream: true` in your request to enable streaming responses.

</details>

<details>

<summary><strong>What SDK support is available?</strong></summary>

Infron AI is a drop-in replacement for OpenAI. Therefore, any SDKs that support OpenAI by default also support Infron AI. Check out our [docs](https://infronai.gitbook.io/docs/frameworks-and-integrations/overview) for more details.

</details>

<details>

<summary><strong>Can I mix different modalities in one request?</strong></summary>

Yes! You can send text, images, PDFs, and audio in the same request. The model will process all inputs together.

</details>

<details>

<summary><strong>Does Infron AI use Prompt Cache by default?</strong></summary>

Yes. Prompt Cache is enabled by default in Infron AI for all API calls. This means that whenever you send a request, Infron AI will attempt to use the cached prompt/response if applicable.

</details>

<details>

<summary><strong>Will using Prompt Cache change my token usage or latency?</strong></summary>

* **Token usage:** When a cached response is served, actual model inference may be skipped, which can reduce token consumption.
* **Latency:** Cached responses are generally faster to return compared to generating new responses from the model.
* **Billing:** The cost per request is based on the Prompt Cache price tier, regardless of cache hit or miss

</details>

<details>

<summary><strong>Can I disable Prompt Cache?</strong></summary>

At this time, Prompt Cache is permanently enabled in Infron AI and cannot be turned off. The design ensures consistent performance optimization and uniform billing.

</details>

### Privacy and Data Logging <a href="#privacy-and-data-logging" id="privacy-and-data-logging"></a>

Please see our [Terms of Service](https://app.onerouter.pro/terms) and [Privacy Policy](https://openrouter.ai/privacy).

<details>

<summary><strong>What data is logged during API use?</strong></summary>

We log basic request metadata (timestamps, model used, token counts). Prompt and completion are not logged by default. We do zero logging of your prompts/completions, even if an error occurs.

</details>

<details>

<summary><strong>What third-party sharing occurs?</strong></summary>

Infron AI is a proxy that sends your requests to the model provider for it to be completed. We work with all providers to, when possible, ensure that prompts and completions are not logged or used for training. Providers that do log, or where we have been unable to confirm their policy, will not be routed to unless the model training toggle is switched on in the [privacy](https://app.onerouter.pro/privacy).

</details>

### Credit and Billing Systems <a href="#credit-and-billing-systems" id="credit-and-billing-systems"></a>

<details>

<summary><strong>What purchase options exist?</strong></summary>

Infron AI uses a credit system where the base currency is US dollars.&#x20;

All of the pricing on our site and API is denoted in dollars. Users can top up their balance manually.

</details>

<details>

<summary><strong>Do credits expire?</strong></summary>

Per our [terms](https://app.onerouter.pro/terms), we reserve the right to expire unused credits after one year of purchase.

</details>

<details>

<summary><strong>My credits haven't showed up in my account</strong></summary>

If you paid using Stripe, sometimes there is an issue with the Stripe integration and credits can get delayed in showing up on your account. Please allow up to one hour. If your credits still have not appeared after an hour, contact us on email and we will look into it.

</details>

<details>

<summary><strong>How to monitor credit usage?</strong></summary>

The [Activity](https://app.onerouter.pro/activity) page allows users to view their historic usage and filter the usage by model, provider and api key.

We also provide a [Logs](https://app.onerouter.pro/logs) page that has live information about the balance and remaining credits for the account.

</details>

<details>

<summary><strong>How do volume discounts work?</strong></summary>

Infron AI does not currently offer volume discounts, but you can reach out to us over email if you think you have an exceptional use case.

</details>

<details>

<summary><strong>What payment methods are accepted?</strong></summary>

We accept all major credit cards, AliPay, PayPal and WechatPay. if there are any payment methods that you would like us to support please reach out on [issue](https://github.com/TrustAI-laboratory/OneRouter/issues).

</details>

### Account Management <a href="#account-management" id="account-management"></a>

<details>

<summary><strong>What analytics are available?</strong></summary>

Our [activity dashboard](https://app.onerouter.pro/index) provides real-time usage metrics. If you would like any specific reports or metrics please contact us.

</details>

<details>

<summary><strong>How can I contact support?</strong></summary>

The best way to reach us is to submit new [issue](https://github.com/TrustAI-laboratory/OneRouter/issues). and email us.

</details>

### Input Format Support <a href="#input-format-support" id="input-format-support"></a>

<details>

<summary>What about video support?</summary>

Video modality support is coming soon! We’re working on adding video processing capabilities to expand our multimodal offerings.

</details>
