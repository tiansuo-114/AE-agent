**[中文文档](README.zh-CN.md) | English**

# AE-Agent

**An AI agent platform for After Effects — run any model, any endpoint, fully under your control.**

[![GitHub Stars](https://img.shields.io/github/stars/tiansuo-114/AE-agent?style=flat-square)](https://github.com/tiansuo-114/AE-agent/stargazers)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue?style=flat-square)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square)](https://github.com/tiansuo-114/AE-agent/pulls)

---

## What is AE-Agent?

AE-Agent brings AI-powered automation directly into After Effects through a CEP panel. Instead of being locked to a single cloud provider, you connect it to **any OpenAI-compatible API** — whether that's Anthropic, a local Ollama instance, or your own self-hosted model.

Ask in natural language. The agent understands your composition, writes and executes the script, and verifies the result visually — all without leaving After Effects.

---

## Features

### 🤖 Multi-Model Agent Engine
- Connects to **Claude Code** or **OpenAI Codex** CLI running locally on your machine
- Switch API endpoints freely via the built-in settings panel
- Supports any OpenAI-compatible base URL (local, cloud, proxy)

### 🎬 Deep After Effects Integration
- Reads full composition structure: layers, effects, keyframes, expressions, masks
- Writes and executes ExtendScript in real time
- Verifies results with live frame previews before reporting success
- Checkpoint system: auto-saves project state before each operation

### 🖼️ Image Generation
- Generate textures, moodboards, and sprites directly in chat
- Auto-imports generated images into the project
- Pluggable image API: swap OpenRouter for any compatible endpoint

### ⚙️ Flexible Configuration
- Floating settings panel — no code editing required
- All keys stored in `localStorage`, never transmitted to third parties
- Separate configuration for chat models and image generation

---

## Supported Capabilities

| Category | What the Agent Can Do |
|----------|-----------------------|
| **Layer Management** | Create, rename, reorganize, batch edit layers |
| **Animation** | Set keyframes, expressions, easing, staggered timing |
| **Effects** | Apply and configure any AE effect by name |
| **Text** | Animate text with per-character control |
| **Shapes** | Build complex shape layers and path animations |
| **Scripting** | Generate and run arbitrary ExtendScript |
| **Keying** | Configure Keylight and other keying effects |
| **Tracking** | Trigger Warp Stabilizer and camera tracker |
| **Images** | Generate and import AI-created assets |

---

## Getting Started

### Requirements

- Windows 10/11 (macOS support planned)
- After Effects 2022+
- Node.js 18+
- One of: Claude Code CLI or OpenAI Codex CLI

```powershell
# Install Claude Code CLI
npm install -g @anthropic-ai/claude-code
```

### Installation

```powershell
# Clone the repo
git clone https://github.com/tiansuo-114/AE-agent.git
cd AE-agent

# Run the installer (sets CEP debug mode + copies files)
.\install.ps1
```

Restart After Effects, then open **Window → Extensions → Atom**.

### Configure Your API

Click the **⚙** button in the panel, or open DevTools console:

```js
// Chat / coding agent
localStorage.setItem('ATOM_API_KEY', 'your-api-key')
localStorage.setItem('ATOM_CUSTOM_BASE_URL', 'https://your-endpoint.com')

// Image generation
localStorage.setItem('ATOM_IMAGE_API_KEY', 'your-image-key')
localStorage.setItem('ATOM_IMAGE_BASE_URL', 'https://openrouter.ai/api/v1')
```

---

## Roadmap

The following is on the horizon — contributions welcome!

- [ ] **macOS installer** — currently Windows only
- [ ] **Gemini CLI support** — add Google Gemini as a third agent option
- [ ] **Premiere Pro port** — apply the same CEP + ExtendScript architecture to Premiere
- [ ] **Skills library** — community-maintained skill packs for common workflows
- [ ] **Video frame analysis** — extract frames via ffmpeg and feed to vision models
- [ ] **Batch mode** — process multiple compositions in queue without supervision
- [ ] **MCP integration** — expose AE operations as Model Context Protocol tools
- [ ] **Plugin awareness** — deeper support for Trapcode, Red Giant, and other third-party effects
- [ ] **Timeline scrubbing via AI** — describe a timing feel and let the agent match it

---

## Community

Join the QQ group to share workflows, ask questions, and connect with other motion designers using AE-Agent.

| | |
|--|--|
| **Group name** | AE-agent 交流群 |
| **Group ID** | `798447894` |

<img src="docs/qq-group.png" width="240" alt="QQ Group QR Code" />

> Scan with QQ app to join directly.

---

## Contributing

This project is in active development and contributions of all kinds are welcome.

### How to contribute

1. **Fork** the repository
2. Create a feature branch: `git checkout -b feature/my-idea`
3. Make your changes
4. Open a **Pull Request** with a clear description

### Good first contributions

- Test on different AE versions and report compatibility
- Improve the patch scripts to support newer Atom releases
- Write Skills (markdown files) for common motion design workflows
- Add macOS support to the install script
- Document edge cases in the wiki

### Found a bug or have an idea?

Open an [Issue](https://github.com/tiansuo-114/AE-agent/issues) — all feedback is appreciated.

---

## Architecture

```
AE-Agent
├── CEP Panel (Svelte/JS)         ← UI running in AE's embedded browser
│   └── main-Bumuo9MN.js          ← Core bundle (patched)
├── ExtendScript Bridge           ← Talks to AE's scripting engine
│   ├── AEKnowledgeExtractorV2    ← Scans composition structure
│   └── Main.jsx                  ← Script runner
└── Agent CLI                     ← Claude Code or Codex (local process)
    └── stdin/stdout JSON stream  ← Communication protocol
```

---

## License

MIT — see [LICENSE](LICENSE)
