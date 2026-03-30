# MMM-AI-Jarvis

A [MagicMirror²](https://magicmirror.builders/) module that integrates Google Cloud Vertex AI with real-time web scraping to provide a voice-activated smart assistant experience.

## Features

- 🎙️ **Voice activation** — wake word detection triggers the assistant
- 🤖 **Google Cloud Vertex AI** — natural language understanding and response generation
- 🌐 **Web scraping** — pulls live data to answer real-world queries
- 💬 **Text-to-speech responses** — assistant speaks answers aloud
- 🪞 **MagicMirror² integration** — displays conversation and status on your mirror

## Prerequisites

- [MagicMirror²](https://magicmirror.builders/) installed and running
- Node.js v16+
- A [Google Cloud](https://cloud.google.com/) account with Vertex AI API enabled
- A service account JSON key with Vertex AI permissions
- A microphone connected to your device

## Installation

1. Clone this module into your MagicMirror modules directory:

```bash
cd ~/MagicMirror/modules
git clone https://github.com/RedNetty/Assistant-Module.git
cd Assistant-Module
npm install
```

2. Add your Google Cloud service account key:

```bash
cp service-account.example.json service-account.json
# Edit service-account.json with your credentials
```

3. Add the module to your MagicMirror `config/config.js`:

```js
{
  module: "Assistant-Module",
  position: "bottom_center",
  config: {
    projectId: "your-gcp-project-id",
    location: "us-central1",
    wakeWord: "hey mirror",
    language: "en-US"
  }
}
```

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| `projectId` | Your Google Cloud project ID | *required* |
| `location` | Vertex AI region | `"us-central1"` |
| `wakeWord` | Phrase to activate the assistant | `"hey mirror"` |
| `language` | BCP-47 language code | `"en-US"` |

## Environment Variables

Set the following before starting MagicMirror:

```bash
export GOOGLE_APPLICATION_CREDENTIALS="/path/to/service-account.json"
```

## Tech Stack

- **MagicMirror²** module framework
- **Google Cloud Vertex AI** for language model inference
- **Node.js** with `node-record-lpcm16` for audio capture
- **Cheerio** / **Puppeteer** for web scraping
