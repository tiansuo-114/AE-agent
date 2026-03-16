**English | [中文文档](README.zh-CN.md)**

# AE-Agent

**面向 After Effects 的 AI Agent 平台 — 使用任意模型、任意端点，完全自主掌控。**

[![GitHub Stars](https://img.shields.io/github/stars/tiansuo-114/AE-agent?style=flat-square)](https://github.com/tiansuo-114/AE-agent/stargazers)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue?style=flat-square)](LICENSE)
[![欢迎 PR](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square)](https://github.com/tiansuo-114/AE-agent/pulls)

---

## 它是什么

AE-Agent 通过 CEP 面板将 AI 自动化能力直接带入 After Effects。不再依赖单一云服务商——你可以接入**任何 OpenAI 兼容的 API**，无论是 Anthropic、本地 Ollama 实例，还是你自己搭建的模型。

用自然语言描述你想要的效果，Agent 会理解合成结构、编写并执行脚本，并通过实时帧预览验证结果——全程无需离开 After Effects。

---

## 功能特性

### 🤖 多模型 Agent 引擎
- 连接本地运行的 **Claude Code** 或 **OpenAI Codex** CLI
- 通过内置设置面板随时切换 API 端点
- 支持任意 OpenAI 兼容的 base URL（本地、云端、代理均可）

### 🎬 深度 AE 集成
- 读取完整合成结构：图层、特效、关键帧、表达式、蒙版
- 实时编写并执行 ExtendScript
- 操作前自动保存 Checkpoint，支持一键回滚
- 通过实时帧预览验证结果，确保所见即所得

### 🖼️ 图像生成
- 直接在聊天界面生成贴图、情绪板、精灵图
- 自动导入生成的图片到 AE 项目
- 可插拔图像 API，替换为任意兼容端点

### ⚙️ 灵活配置
- 悬浮设置面板——无需编辑代码
- 所有密钥存储在 `localStorage`，不传输给第三方
- 聊天模型与图像生成分别独立配置

---

## 支持的操作能力

| 类别 | Agent 能做什么 |
|------|--------------|
| **图层管理** | 创建、重命名、重组、批量编辑图层 |
| **动画制作** | 设置关键帧、表达式、缓动、错开时序 |
| **特效配置** | 按名称应用并调整任意 AE 内置特效 |
| **文字动画** | 逐字符控制的文字动画 |
| **形状图层** | 构建复杂形状图层和路径动画 |
| **脚本执行** | 生成并运行任意 ExtendScript |
| **抠像处理** | 配置 Keylight 等抠像特效 |
| **跟踪稳定** | 触发 Warp Stabilizer、摄像机跟踪 |
| **图像资产** | 生成并导入 AI 创建的素材 |

---

## 快速开始

### 环境要求

- Windows 10/11（macOS 支持开发中）
- After Effects 2022 或更高版本
- Node.js 18+
- Claude Code CLI 或 OpenAI Codex CLI 之一

```powershell
# 安装 Claude Code CLI
npm install -g @anthropic-ai/claude-code
```

### 安装步骤

```powershell
# 克隆仓库
git clone https://github.com/tiansuo-114/AE-agent.git
cd AE-agent

# 运行安装脚本（设置 CEP 调试模式 + 复制文件）
.\install.ps1
```

重启 After Effects，打开 **窗口 → 扩展 → Atom**。

### 配置你的 API

点击面板中的 **⚙** 按钮，或在 DevTools 控制台中执行：

```js
// 聊天 / 编码 Agent
localStorage.setItem('ATOM_API_KEY', '你的-api-key')
localStorage.setItem('ATOM_CUSTOM_BASE_URL', 'https://你的端点.com')

// 图像生成
localStorage.setItem('ATOM_IMAGE_API_KEY', '你的-图像-key')
localStorage.setItem('ATOM_IMAGE_BASE_URL', 'https://openrouter.ai/api/v1')
```

---

## 路线图

以下功能正在规划中，欢迎一起参与！

- [ ] **macOS 安装脚本** — 目前仅支持 Windows
- [ ] **Gemini CLI 支持** — 添加 Google Gemini 作为第三种 Agent 选项
- [ ] **Premiere Pro 适配** — 将同样的 CEP + ExtendScript 架构迁移到 PR
- [ ] **Skills 库** — 社区维护的工作流技能包
- [ ] **视频帧分析** — 通过 ffmpeg 提取帧并送入视觉模型
- [ ] **批处理模式** — 无人值守地批量处理多个合成
- [ ] **MCP 集成** — 将 AE 操作暴露为 Model Context Protocol 工具
- [ ] **第三方插件感知** — 更深度支持 Trapcode、Red Giant 等插件
- [ ] **时序语音控制** — 描述节奏感，让 Agent 自动匹配

---

## 💬 社区交流

加入 QQ 群，分享工作流程、提问、和其他 AE 用户交流。

| | |
|--|--|
| **群名** | AE-agent 交流群 |
| **群号** | `798447894` |

<img src="docs/qq-group.png" width="240" alt="QQ 群二维码" />

> 用 QQ 扫一扫直接加入。

**微信群**

<img src="docs/wechat-group.jpg" width="240" alt="微信群二维码" />

> 用微信扫一扫直接加入。

---

## 参与贡献

项目正在积极开发中，欢迎各种形式的贡献。

### 如何贡献

1. **Fork** 本仓库
2. 创建功能分支：`git checkout -b feature/你的想法`
3. 完成修改
4. 提交 **Pull Request**，附上清晰的说明

### 适合新手的贡献方向

- 在不同 AE 版本上测试并反馈兼容性
- 为更新版本的 Atom 适配补丁脚本
- 编写 Skills（Markdown 文件）覆盖常用动态设计工作流
- 完善 install.ps1 添加 macOS 支持
- 在 Wiki 中记录边界情况

### 发现了 Bug 或有新想法？

欢迎提交 [Issue](https://github.com/tiansuo-114/AE-agent/issues)，所有反馈都很有价值。

---

## 技术架构

```
AE-Agent
├── CEP 面板（Svelte/JS）          ← 运行在 AE 内嵌浏览器中的 UI
│   └── main-Bumuo9MN.js          ← 核心 bundle
├── ExtendScript 桥               ← 与 AE 脚本引擎通信
│   ├── AEKnowledgeExtractorV2    ← 扫描合成结构
│   └── Main.jsx                  ← 脚本执行器
└── Agent CLI                     ← Claude Code 或 Codex（本地进程）
    └── stdin/stdout JSON 流      ← 通信协议
```

---

## License

MIT — 详见 [LICENSE](LICENSE)
