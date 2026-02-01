# Realigns AI API – v2.0  Licensed Realigns Inc 2026-

### Official Guide for Developers and Customers  
Test Api (limited Free) ```https://realignsinc.com/free-gpt/```
About api: ```https://realignsinc.com/gpt-api/  ```

Email to apply for API key: ```support@realignsinc.com```

---

![version](https://img.shields.io/badge/version-v2.0-blue)
![status](https://img.shields.io/badge/status-active-success)
![license](https://img.shields.io/badge/license-Proprietary-lightgrey)

---

## About Realigns AI API

The **Realigns AI API** is a secure, enterprise-grade AI gateway developed by **Realigns Inc.** to integrate AI chat, assistants, and automation into any software environment — without relying on costly providers such as Gemini, Claude, DeepSeek, Meta, or OpenAI.

### Core Advantages
- Managed by Realigns AI Lab 
- Secure API key authentication  
- Abuse and rate-limit protection  
- Centralized billing system  
- Model-agnostic (GPT / Local LLM / Hybrid)

---

## Use Cases

| Platform | Common Integrations |
|-----------|--------------------|
| **Websites** | Chatbots, lead capture, FAQ automation |
| **WordPress** | AI widgets, support agents, admin assistants |
| **Mobile / Systems** | iOS & Android apps, CRM / ERP integration, HR automation |

---

## Secure API Key Usage

Use your API key **only on trusted backend servers** or secured environments:
- Node.js / PHP / Python backend  
- WordPress `functions.php` or secured plugins  
- AWS / VPS / Cloud servers via environment variables  

### **Base Endpoint**
```

POST https://gpt-api.realignsinc.com/ai/chat
```

**Headers**
```
x-api-key: YOUR_API_KEY
Content-Type: application/json

```
---

## 🚫 Forbidden Usage (Security Rules)

Do **NOT** expose your API key publicly.  
Violations will result in **immediate revocation**.

- ❌ Client-side JavaScript  
- ❌ Public HTML or browser console logs  
- ❌ Mobile apps without proxy layer  
- ❌ Public GitHub repositories  

---

## Basic API Request Format

**Method:** POST  
**URL:** `https://gpt-api.realignsinc.com/ai/chat`

### Example Request
```json
{
  "prompt": "Hello, explain your services"
}

```
Example Response

```
{
  "reply": "Hello! Realigns provides AI-powered solutions including..."
}


```
Example Integrations
🟦 PHP (WordPress)
```
$response = wp_remote_post(
  'https://gpt-api.realignsinc.com/ai/chat',
  array(
    'headers' => array(
      'Content-Type' => 'application/json',
      'x-api-key'    => 'YOUR_API_KEY'
    ),
    'body' => json_encode(array(
      'prompt' => 'Explain Realigns services'
    ))
  )
);
```

🟩 Node.js
```
fetch("https://gpt-api.realignsinc.com/ai/chat", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
    "x-api-key": process.env.REALIGNS_API_KEY
  },
  body: JSON.stringify({ prompt: "Hello AI" })
});
```

🟨 Kotlin (Android)
```
import okhttp3.*
import org.json.JSONObject
import java.io.IOException

class RealignsAI {
    private val client = OkHttpClient()

    fun sendPrompt(prompt: String, apiKey: String, callback: (String?) -> Unit) {
        val url = "https://gpt-api.realignsinc.com/ai/chat"
        val json = JSONObject().put("prompt", prompt)
        val body = RequestBody.create(MediaType.parse("application/json"), json.toString())

        val request = Request.Builder()
            .url(url)
            .post(body)
            .addHeader("x-api-key", apiKey)
            .addHeader("Content-Type", "application/json")
            .build()

        client.newCall(request).enqueue(object : Callback {
            override fun onFailure(call: Call, e: IOException) {
                callback("Error: ${e.message}")
            }

            override fun onResponse(call: Call, response: Response) {
                val result = response.body()?.string()
                callback(result)
            }
        })
    }
}

// Usage Example:
val ai = RealignsAI()
ai.sendPrompt("Describe Realigns AI", "YOUR_API_KEY") {
    println(it)
}
```
🐍 CodeX (Python SDK)
```
import requests
import json

API_URL = "https://gpt-api.realignsinc.com/ai/chat"
HEADERS = {
    "x-api-key": "YOUR_API_KEY",
    "Content-Type": "application/json"
}

data = {"prompt": "Explain Realigns services"}

response = requests.post(API_URL, headers=HEADERS, data=json.dumps(data))

if response.status_code == 200:
    print(response.json()["reply"])
else:
    print("Error:", response.text)

```
Install Dependency
```
pip install requests

```

Usage Rules & Fair Policy

All API keys are subject to rate limits and abuse monitoring.

🚫 Prohibited Activities (Permanent Blocked)

❌ Illegal or violent content

❌ Adult or explicit material

❌ Hacking or malware generation

❌ Political manipulation or propaganda

❌ Unlicensed medical advice

Support & Contact

Email: distribution@api.realignsinc.com - support@realignsinc.com

URL: https://www.realignsinc.com -  https://ai.realignsinc.com

Developed by; REALIGNS AL LAB- International 2024-2025

© Realigns Inc. – 2026 | All rights reserved.

