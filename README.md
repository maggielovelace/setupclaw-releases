# SetupClaw Releases

Official downloads for **SetupClaw**, the desktop setup wizard and management UI for OpenClaw.

> Source code lives in a private repository. This repo contains only binary releases, changelog, and issue tracking for download/install/update problems.

**Website:** https://setupclaw.uk — [English](https://setupclaw.uk/en/app) · [中文](https://setupclaw.uk/zh/app)

---

## Screenshots

A tour of the main surfaces inside SetupClaw. Every screen is designed for zero-CLI operation — everything you'd normally do with `openclaw` commands is a click away.

### Dashboard

<p align="center">
  <img src="screenshots/1-dashboard-mockup.png" alt="SetupClaw dashboard — gateway status, active model, channel count, AI provider catalog, quick actions, and developer panel" width="820">
</p>

Your OpenClaw command center. Gateway health at a glance, active model pin, channel count, a catalog of every configured AI provider, plus quick actions for self-repair, plugin environment repair, and force restart.

### Chat

<p align="center">
  <img src="screenshots/2-chat-session-mockup.png" alt="SetupClaw chat — sidebar with all sessions, status filters, labels, and an active conversation thread" width="820">
</p>

A full chat surface built on top of OpenClaw's session API. Browse every session across every agent, filter by status and labels, flag conversations, and jump straight into the thread without leaving the desktop.

### IM Channels

<p align="center">
  <img src="screenshots/3-IM-channels-mockup.png" alt="SetupClaw IM channels — guided wizards for 9 messaging platforms" width="820">
</p>

Connect SetupClaw to **9 messaging platforms** through guided wizards: Feishu, DingTalk, WeChat Work, QQ, Personal WeChat, Telegram, Discord, Slack, and WhatsApp. No plugin manifest editing, no credential JSON files, no CLI flags.

### Agents

<p align="center">
  <img src="screenshots/4-agents-mockup.png" alt="SetupClaw agents — AI agent dashboard with per-agent model, persona, tool policies, and route bindings" width="820">
</p>

Full lifecycle management for OpenClaw's native AI agents. Create agents through a guided wizard with bundled templates, manage per-agent models, personas, tool policies, and multi-factor route bindings.

### Models & APIs

<p align="center">
  <img src="screenshots/5-models-APIs-mockup.png" alt="SetupClaw models — every OpenClaw-supported AI provider with verification state and API key management" width="820">
</p>

Every model OpenClaw supports, in one place. Verify API keys, add custom models, switch between provider variants, and authorize OAuth providers with one click.

### Skills

<p align="center">
  <img src="screenshots/6-skills-mockup.png" alt="SetupClaw skills — skill extensions from various sources with install, enable, and update management" width="820">
</p>

Manage skill extensions — Claude Code plugins, MCP servers, tool catalogs, and anything else OpenClaw can load as a skill. Install from the public registry, import locally, enable per agent, update with one click.

### Settings

<p align="center">
  <img src="screenshots/7-settings-mockup.png" alt="SetupClaw settings — language, theme, data backup, update preferences, and advanced OpenClaw configuration" width="820">
</p>

Language (English / 中文), theme, data backup (manual + automatic), auto-update preferences, and the full set of advanced OpenClaw runtime knobs.

---

## Download

- **macOS (universal, Intel + Apple Silicon):** [SetupClaw-Lite.dmg](https://github.com/maggielovelace/setupclaw-releases/releases/latest/download/SetupClaw-Lite.dmg)
- **Windows:** Coming soon
- **Linux:** Coming soon

See [all releases](https://github.com/maggielovelace/setupclaw-releases/releases) for version history.

## System Requirements

- **macOS:** 11 Big Sur or later, Intel or Apple Silicon

## Install Instructions

1. Click the macOS download link above.
2. Open the downloaded `.dmg`.
3. Drag `SetupClaw` to your `Applications` folder.
4. On first launch, macOS may ask you to confirm opening an app downloaded from the internet — click **Open**. The app is signed and notarized by Apple's notary service, so you will not see a "cannot be opened because the developer cannot be verified" dialog.

## Verifying the Signature (optional, for security-conscious users)

After installing, verify the signature and notarization from a terminal:

```bash
codesign --verify --deep --strict --verbose=2 /Applications/SetupClaw.app
spctl --assess --type execute --verbose /Applications/SetupClaw.app
```

Both commands should report success and show the Developer ID certificate.

## Auto-Update

Once installed, SetupClaw checks for updates automatically and will prompt you when a new version is available. See [SECURITY.md](SECURITY.md) for details on how auto-update integrity is verified.

## Reporting Problems

- **Download or install issues:** [Open an issue](https://github.com/maggielovelace/setupclaw-releases/issues/new?template=download-issue.md)
- **Auto-update failures:** [Open an issue](https://github.com/maggielovelace/setupclaw-releases/issues/new?template=update-issue.md)
- **Feature requests or in-app bugs:** Contact support via https://setupclaw.uk

---

# SetupClaw 发布仓库

**SetupClaw** 官方安装包下载 — 用于 OpenClaw 的桌面端安装向导与管理界面。

> 源代码托管在私有仓库中，本仓库仅用于发布安装包、变更记录和下载/安装/更新问题的 issue 跟踪。

**官网：** https://setupclaw.uk — [English](https://setupclaw.uk/en/app) · [中文](https://setupclaw.uk/zh/app)

## 应用截图

下面是 SetupClaw 主要界面的一组预览。所有功能都是零命令行操作 — 本来要敲 `openclaw` 命令的事情，都做成了一键点击。

### 功能面板

<p align="center">
  <img src="screenshots/1-dashboard-mockup.png" alt="SetupClaw 功能面板 — Gateway 状态、激活模型、渠道数量、AI 提供商目录、快捷操作与开发者面板" width="820">
</p>

OpenClaw 的指挥中心。一眼看到 Gateway 状态、当前激活的模型、渠道数量，以及所有已配置的 AI 提供商目录。快捷操作一键自修复、修复插件环境、强制重启。

### 会话

<p align="center">
  <img src="screenshots/2-chat-session-mockup.png" alt="SetupClaw 会话 — 会话列表、状态筛选、标签、当前对话线程" width="820">
</p>

基于 OpenClaw Session API 构建的完整会话界面。一个地方浏览所有智能体的所有会话，按状态和标签筛选，标记重点对话，直接在桌面端进入对话。

### IM 渠道

<p align="center">
  <img src="screenshots/3-IM-channels-mockup.png" alt="SetupClaw IM 渠道 — 飞书、钉钉、企业微信、QQ、个人微信、Telegram、Discord、Slack、WhatsApp 九大平台引导式向导" width="820">
</p>

通过引导式向导一键接入 **9 大消息平台**：飞书、钉钉、企业微信、QQ、个人微信、Telegram、Discord、Slack、WhatsApp。无需编辑插件清单、无需填写凭证 JSON、无需命令行参数。

### 智能体

<p align="center">
  <img src="screenshots/4-agents-mockup.png" alt="SetupClaw 智能体 — AI 智能体面板，支持独立模型、人设、工具策略与路由规则" width="820">
</p>

OpenClaw 原生智能体的全生命周期管理。通过引导式向导 + 内置模板快速创建，独立管理每个智能体的模型、人设、工具策略和多维路由绑定。

### 模型与 API

<p align="center">
  <img src="screenshots/5-models-APIs-mockup.png" alt="SetupClaw 模型 — OpenClaw 支持的所有 AI 提供商，包含验证状态与密钥管理" width="820">
</p>

在一个地方管理 OpenClaw 支持的所有模型。校验 API 密钥、添加自定义模型、在提供商变体之间切换，支持 OAuth 一键授权。

### 技能

<p align="center">
  <img src="screenshots/6-skills-mockup.png" alt="SetupClaw 技能 — 从多来源管理 skill 扩展，一键安装、启用与更新" width="820">
</p>

管理 skill 扩展 — Claude Code 插件、MCP 服务器、工具目录，以及任何 OpenClaw 可以作为 skill 加载的组件。从公开注册中心安装、从本地导入、按智能体启用、一键更新。

### 设置

<p align="center">
  <img src="screenshots/7-settings-mockup.png" alt="SetupClaw 设置 — 语言、主题、数据备份、更新偏好与 OpenClaw 高级配置" width="820">
</p>

语言（英文 / 中文）、主题（深色 / 浅色）、数据备份（手动 + 自动）、自动更新偏好，以及完整的 OpenClaw 运行时高级选项。

## 下载

- **macOS（通用，Intel + Apple Silicon）：** [SetupClaw-Lite.dmg](https://github.com/maggielovelace/setupclaw-releases/releases/latest/download/SetupClaw-Lite.dmg)
- **Windows：** 即将推出
- **Linux：** 即将推出

## 系统要求

- **macOS：** 11 Big Sur 或更高版本，Intel 或 Apple Silicon

## 安装步骤

1. 点击上面的 macOS 下载链接。
2. 打开下载的 `.dmg` 文件。
3. 将 `SetupClaw` 拖到 `应用程序` 文件夹中。
4. 首次启动时，macOS 可能会询问是否打开从互联网下载的应用 — 点击 **打开**。本应用已经过 Apple 签名并公证。
