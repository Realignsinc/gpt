<p align="center">
  <img src="Realigns%20v2o.jpg" alt="Realigns v2.0 Banner" width="100%">
</p>



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
| **IoT / Industrial Systems** | Smart kiosks, factory terminals, warehouse devices, access panels, voice-enabled machines, sensor-triggered assistants |

### Industrial & Cost Advantage

- Designed for **industrial and embedded environments** where cloud dependency is limited or costly  
- Suitable for **factories, warehouses, retail kiosks, logistics hubs, and smart equipment**
- API pricing is **approximately 60–80% lower** than traditional AI providers’ token-based billing
- Predictable usage models ideal for **always-on devices** and **high-frequency requests**
- Enables AI features without the operational cost burden of mainstream APIs

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

## 🎙 Realigns GPT v2o – Voice TTS API (Beta)

**Engine:** Piper TTS  
**Voice:** US English (Ryan)  
**Output:** Raw WAV audio  
**Use Case:** Voice assistants, kiosks, IoT devices, IVR, accessibility, AI agents

---

### 🔊 Supported Voice (Current)

- **Language:** `en-US`
- **Model Mapping:** `en_US-ryan-medium.onnx`
- **Quality:** Natural, neutral US accent
- **Text Limit:** ~400 characters per request (validated server-side)

> Additional voices and languages (e.g. Urdu) can be enabled in future versions behind the `lang` field.

---

## Endpoint

```http
POST https://gpt-api.realignsinc.com/voice/tts
```
Required Headers
```
Content-Type: application/json
x-api-key: YOUR_REALIGNS_API_KEY
```
Request Body
```
{
  "text": "This is Realigns AI speaking.",
  "lang": "en-US"
}
```
Field	Type	Required	Notes
text	string	✅	Max ~400 characters
lang	string	optional	Default: en-US
Response

Content-Type: `audio/wav`

Body: `Binary WAV audio stream`

Example headers:
```
Content-Type: audio/wav
Content-Disposition: inline; filename="voice.wav"
```
Voice Integration Methods
```
1️⃣ cURL (Save WAV to file)
curl -X POST https://gpt-api.realignsinc.com/voice/tts \
  -H "Content-Type: application/json" \
  -H "x-api-key: YOUR_REALIGNS_API_KEY" \
  -d '{"text":"This is Realigns AI speaking.","lang":"en-US"}' \
  --output voice-test.wav
```
2️⃣ PHP (WordPress / Backend)
```
<?php
$api_url = 'https://gpt-api.realignsinc.com/voice/tts';
$api_key = 'YOUR_REALIGNS_API_KEY';

$payload = [
  'text' => 'Welcome to Realigns AI voice.',
  'lang' => 'en-US',
];

$response = wp_remote_post($api_url, [
  'headers' => [
    'Content-Type' => 'application/json',
    'x-api-key'    => $api_key,
  ],
  'body'    => json_encode($payload),
  'timeout' => 60,
]);

if (is_wp_error($response)) {
  error_log('TTS error: ' . $response->get_error_message());
  return;
}

$audio = wp_remote_retrieve_body($response);
file_put_contents(WP_CONTENT_DIR . '/uploads/realigns-tts.wav', $audio);
```
3️⃣ Browser JavaScript (Direct Playback)
```
async function speakWithRealigns(text) {
  const res = await fetch("https://gpt-api.realignsinc.com/voice/tts", {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      "x-api-key": "YOUR_REALIGNS_API_KEY",
    },
    body: JSON.stringify({ text, lang: "en-US" }),
  });

  if (!res.ok) {
    console.error("TTS error:", await res.text());
    return;
  }

  const audioBlob = await res.blob();
  const audio = new Audio(URL.createObjectURL(audioBlob));
  audio.play();
}

// Example usage
speakWithRealigns("Realigns AI voice is now live.");
```
4️⃣ Node.js (Save WAV to Disk)
```
import fs from "fs";
import fetch from "node-fetch";

async function generateTts() {
  const res = await fetch("https://gpt-api.realignsinc.com/voice/tts", {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      "x-api-key": "YOUR_REALIGNS_API_KEY",
    },
    body: JSON.stringify({
      text: "This is Realigns AI speaking from Node.js.",
      lang: "en-US",
    }),
  });

  if (!res.ok) {
    console.error("TTS error:", await res.text());
    return;
  }

  const buffer = Buffer.from(await res.arrayBuffer());
  fs.writeFileSync("voice-test.wav", buffer);
  console.log("Saved voice-test.wav");
}

generateTts();
```
## ⚠️ Notes for Production


Use backend or gateway proxy for mobile & IoT devices

Avoid exposing API keys in firmware or frontend apps

Designed for short, real-time speech (assistants, alerts, responses)



##  Rules & Fair Policy

All API keys are subject to rate limits and abuse monitoring.

🚫 Prohibited Activities (Permanent Blocked)

❌ Illegal or violent content

❌ Adult or explicit material

❌ Hacking or malware generation

❌ Political manipulation or propaganda

❌ Unlicensed medical advice

## Support & Contact

Email: distribution@api.realignsinc.com - support@realignsinc.com

URL: https://www.realignsinc.com -  https://ai.realignsinc.com

Developed by; REALIGNS AL LAB- International 2024-2025

📄 License

This gateway wraps local models and open-source components like llama.cpp and piper-tts.
Please respect all upstream licenses for models and libraries you use.

© Realigns Inc. – 2026 | All rights reserved.

