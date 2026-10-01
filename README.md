# ClaudeOpen

ClaudeOpen is a lightweight, Claude-inspired chat interface that runs as a static web app and connects to **OpenAI-compatible** `/chat/completions` APIs.

## Features

- Claude-inspired dark interface
- OpenAI-compatible provider support
- Streaming responses
- Custom model ID and system prompt
- Conversation history
- Markdown and code blocks
- Copy buttons for generated code
- Generated-file cards with preview/download
- Static deployment through GitHub Pages
- No build step or framework required

## Live site

GitHub Pages is enabled for this repository:

**https://madgeret-del.github.io/ClaudeOpen/**

## Use

1. Open the site.
2. Open **Settings**.
3. Enter an OpenAI-compatible base URL.
4. Enter your API key.
5. Select or enter a model ID.
6. Start chatting.

The app automatically appends `/chat/completions` when needed.

## Local development

No dependencies are required. Clone the repository and serve it with any static HTTP server.

```bash
git clone https://github.com/madgeret-del/ClaudeOpen.git
cd ClaudeOpen
python -m http.server 8000
```

Then open `http://localhost:8000`.

## Browser storage

Settings and conversations are saved locally in your browser using a small async storage adapter backed by `localStorage` when `window.storage` is unavailable.

> **Security note:** an API key entered into the app is stored in the browser. Use keys with limited permissions/credits and do not use this app on an untrusted device or shared browser profile.

## Provider compatibility

ClaudeOpen expects an OpenAI-style endpoint roughly compatible with:

```http
POST /chat/completions
Authorization: Bearer YOUR_KEY
Content-Type: application/json
```

Streaming uses server-sent data chunks compatible with the common OpenAI `choices[0].delta.content` format.

## Project structure

```text
ClaudeOpen/
├─ index.html
├─ README.md
└─ .github/
   └─ workflows/
      └─ static.yml
```

The current app is intentionally self-contained in `index.html`. A future cleanup can split styles, scripts, and embedded assets into separate files without changing functionality.

## Disclaimer

ClaudeOpen is an independent project and is **not affiliated with Anthropic**. “Claude” and related marks belong to their respective owners.
