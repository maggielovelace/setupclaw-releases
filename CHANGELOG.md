# Changelog

All notable changes to SetupClaw will be documented here. New entries are appended at the top.

## Unreleased

Planned changes land here until they ship in a tagged release.

## v2026.4.900 — 2026-04-09 — First Public Release

> **Overview:** First public release of SetupClaw Desktop — a GUI setup wizard and management console for OpenClaw. This release ships a full Chat interface, a 9-platform IM channel manager, the Agents dashboard with a guided builder, a redesigned dashboard and welcome experience, and fully wired auto-update via GitHub Releases. Available for macOS 11+ (Intel and Apple Silicon), signed and notarized by Apple.

---

### 🎉 New features

#### Chat

- **Complete Chat interface** — three-column layout (session sidebar, message view, metadata panel) with TorlyAI-style visual polish, rounded panels, and consistent shadows. Session cards are borderless, compact, and show preview text + timestamps.
- **Rich markdown rendering** — chat messages render full GitHub-flavored markdown via `react-markdown` + `remark-gfm`. Code blocks, tables, task lists, strikethrough, and inline code all render correctly. OpenClaw framework tags are stripped from visible text.
- **Session header with full context** — displays `Session Name (Channel · Agent · MM/DD)`, falling back to the agent name when a session is unnamed. Inline rename with auto-focus.
- **Metadata panel** — shows Session ID, creation date + time, current channel source (SetupClaw Desktop, OpenClaw Web, or an IM platform), custom labels, and status flags.
- **Custom labels system** — create, persist, and filter sessions by user-defined labels. Label management lives in Settings.
- **Session pagination** — lists load the first 20 sessions instantly, with "Load More" for the rest. No more blank flashes on slow networks.
- **Agent selector dropdown** at the bottom of the chat sidebar for quickly switching the active agent without leaving the chat view.
- **Inline file access** — the Files tab opens the workspace folder directly, with the current chat transcripts subfolder pre-selected in Finder.
- **Channel attribution** — sessions correctly distinguish between SetupClaw Desktop, OpenClaw Web Chat, and all 9 IM channels. "Show in Finder" opens the OpenClaw sessions directory for the correct source.
- **Inline model selector** in the chat composer — friendly model names grouped by provider (OpenAI, Anthropic, Google, Qwen, etc.).
- **Optimistic updates** for status, flag, label, archive, and rename actions — UI responds instantly and survives page reloads.

#### Channels

- **Redesigned Channels page** — sidebar + content panel layout replacing the old flat list. Grouped by category (Work, Social, International) with responsive collapse (300px → 220px → 56px icon-only) and full keyboard navigation.
- **Guided setup wizard** — 8-step modal wizard for all 9 supported IM platforms with per-channel credential forms, validation, and recovery flows for degraded channels.
- **Nine supported platforms:**
  - **Work (China):** Feishu, WeCom (企业微信), DingTalk
  - **Social (China):** Personal WeChat, QQ
  - **International:** Telegram, Discord, Slack, WhatsApp
- **Account detail cards** — row-based display with degraded-state alert banners, disabled-state styling, and progressive disclosure for advanced settings.
- **Plugin lifecycle management** — automatic detection of installed/registered/loaded/ready states for managed channel plugins, with repair and recovery for degraded plugins.
- **21+ OpenClaw IM channels mapped** — chat session metadata recognizes and labels every channel from the OpenClaw extensions catalog.

#### Agents

- **Full Agents dashboard** at `/agents` with routing agents, health, cron, and activity sections.
- **6-step Agent Builder Wizard** — Purpose → Template → Config → Channels → Persona → Deploy. Four bundled templates covering common use cases (assistant, operator, reviewer, custom).
- **Per-agent configuration modals:**
  - **Model selector** — 4-tier resolution with automatic fallback chain
  - **Persona editor** — edits all 8 workspace markdown files (AGENTS.md, SOUL.md, TOOLS.md, IDENTITY.md, USER.md, HEARTBEAT.md, MEMORY.md, BOOTSTRAP.md)
  - **Tool policy editor** — per-agent tool profiles with allow/deny lists
  - **Route bindings editor** — multi-factor matching (peer > guild+roles > guild > team > account > channel > default)
  - **Cron job editor** — scheduled jobs via `cron.*` RPC
- **Health panel** with gateway heartbeat configuration.
- **Activity log** with real-time gateway RPC events.
- **Verified badge** — agents listed via the `openclaw` CLI show a green "OpenClaw ✓" badge confirming they are registered in the authoritative config.

#### Dashboard

- **Redesigned Dashboard** with KPI tiles (active agents, active channels, gateway status, recent activity), provider cards for quick model configuration, and quick-action buttons for common workflows.
- **Plugin Center** tile showing installed OpenClaw plugins.
- **Gateway status indicator** in the header with degraded-state messaging.

#### Welcome and setup wizard

- **Redesigned Welcome page** with a two-column card layout explaining what SetupClaw does and guiding new users into the setup wizard.
- **Skip welcome for returning users** — the app remembers if a user has completed setup and takes them straight to the dashboard on subsequent launches.
- **Expanded Environment Check page** — deeper verification of Node version, Python availability, Git, OpenClaw CLI, gateway health, and network connectivity, with actionable error messages and one-click fix suggestions where possible.
- **Linear setup wizard flow:** Welcome → Environment Check → API Keys → Channel Connect → Pairing Code → Dashboard.

#### Auto-update

- **Automatic updates via GitHub Releases** — installed SetupClaw checks this repository for new versions and prompts you when one is available. Downloads are verified by SHA-512 before install, and every build is signed and notarized by Apple.
- **Bilingual update prompts** — update dialogs respect the app's language setting.
- **Manual download fallback** — if auto-update fails, the update prompt includes a direct download link so you can grab the `.dmg` yourself.

#### Internationalization

- **Full English and Simplified Chinese localization** across 16 namespaces: common, tooltips, settings, welcome, envCheck, setup, bootstrap, dashboard, chat, models, channels, skills, agents, components, errors, and electron.
- **200+ translation keys for the Agents dashboard** alone.
- **Language switcher in Settings** — changes take effect immediately in both the renderer UI and the main process (tray menu, notifications, dialogs).

#### Under the hood

- **Electron 41** and **electron-builder 26** — latest LTS runtime with improved sandboxing and fluid memory usage.
- **Mantine 8.3** component library with a custom dark theme.
- **Vite 5** with HMR for dev builds.
- **React Router 7** with HashRouter for Electron compatibility.
- **CalVer versioning** — release versions use a `YYYY.M.{day×100+sequence}` format (e.g., `2026.4.900`) that encodes the build date and daily sequence while remaining valid semver for auto-update comparisons.

---

### 🐛 Bug fixes

#### Chat

- Fixed chat session list flashing blank on slow networks — now shows a loading skeleton until sessions arrive.
- Fixed "white screen of death" on first launch caused by an aggressive `localStorage` persistence layer.
- Fixed optimistic updates being overwritten by delayed server reloads.
- Fixed context menu stealing clicks due to incorrect z-index on the backdrop.
- Fixed context menu not closing on outside click.
- Fixed context menu submenus opening off-screen — now positioned correctly with native Mantine behavior.
- Fixed rename action losing focus immediately after opening.
- Fixed "regenerate title" action breaking session lists.
- Fixed an aggressive session filter that caused data loss on the session list.
- Fixed `null` session entries in the API response crashing the chat UI.
- Fixed Mantine `Select` crashing when passed `undefined` data.
- Fixed the model option `group` field crashing Mantine `Select` on older versions.
- Fixed "AI is thinking" label showing for SetupClaw agents — now reads "Claw Agent is thinking" and heartbeat messages are hidden from the visible timeline.
- Fixed the trash button leaking into the chat composer.
- Fixed a stray JSX closing bracket causing a transform error on chat view mount.
- Fixed missing `IconChevronRight` import in `ChatLeftSidebar`.

#### Channels

- Fixed the Discord and QQ channel detection so their sessions correctly attribute to the right platform.
- Fixed session keys being parsed too narrowly, missing channels with non-standard ID formats.
- Fixed "Show in Finder" opening the wrong directory for IM channel sessions.
- Fixed the WeChat Work plugin icon alias — `openclaw-weixin` now resolves correctly in the channel icon picker.

#### Agents

- Fixed the agent dropdown not updating when a new agent was created via the builder wizard.

#### General UI

- Fixed the Welcome page showing every launch for returning users.
- Fixed the Status and Labels sections in the chat metadata panel always collapsing on reload — now they stay expanded by default.
- Fixed session cards showing browser-default button borders.
- Fixed session card spacing to match the TorlyAI reference design.
- Fixed `window.prompt` and `window.confirm` dialogs being used in Electron (where they produce ugly native dialogs) — replaced with Mantine modal components throughout.

#### Auto-update

- Fixed the update service incorrectly reporting "auto-update not configured" when the publish provider was set to `github` (it previously only recognized the `generic` provider with a `url:` field).
- Fixed the placeholder `https://example.invalid/...` publish URL that shipped in early builds — SetupClaw now publishes to and updates from `maggielovelace/setupclaw-releases`.

---

### ⚡ Improvements

- **Refined visual polish pass** — rounded panels, consistent shadow depth, a new `LogoSpinner` component, and a refactored `LoadingScreen` that uses it.
- **Model selector rewrite** — friendly display names grouped by provider, replacing the raw model ID list.
- **Session card rewrite** — borderless EntityRow layout matching the TorlyAI reference, with subtle separators between cards and improved hover states.
- **Settings page** — new Custom Labels management section, improved language switcher.
- **OpenClaw version policy** — clearer compatibility messaging and recovery flows when the bundled OpenClaw CLI version is older or newer than SetupClaw's expected range.
- **Gateway streaming chat transport** — more reliable reconnection after gateway restarts and better handling of partial messages.
- **Combined update orchestrator** — smoother concurrent updates when both SetupClaw and the bundled OpenClaw CLI have new versions available.
- **Plugin install safety** — additional validation before installing managed IM channel plugins to prevent partial installs from corrupting the channel registry.
- **Chat message streaming** — reduced jitter during long-running assistant responses.

---

### 💾 System requirements

- **macOS:** 11 Big Sur or later. Universal binary — works on both Intel and Apple Silicon.
- **Disk space:** ~400 MB for the application, additional space for OpenClaw runtime and model caches.
- **Network:** required for initial setup (downloading OpenClaw dependencies, fetching API keys) and for auto-update checks.

---

### 📦 Download

- [**SetupClaw-Lite.dmg**](https://github.com/maggielovelace/setupclaw-releases/releases/latest/download/SetupClaw-Lite.dmg) — signed + notarized macOS installer
- See the [README](README.md) for install instructions.

---

### 🔐 Verification

After installing, you can verify the signature and notarization from a terminal:

```bash
codesign --verify --deep --strict --verbose=2 /Applications/SetupClaw.app
spctl --assess --type execute --verbose /Applications/SetupClaw.app
```

Both commands should succeed and report the Developer ID certificate.

---

### 🙏 Credits

SetupClaw builds on [OpenClaw](https://openclaw.co), the open-source AI assistant platform. This release is a branded fork of the upstream Qclaw desktop app with localization, channel management, and agent lifecycle improvements added.

---

## 首次公开发布 — 中文说明

### 🎉 新功能亮点

#### 聊天
- **全新聊天界面** — 三列式布局（会话侧栏、消息视图、元数据面板），采用 TorlyAI 风格的视觉设计，圆角面板和一致的阴影效果。
- **完整 Markdown 渲染** — 聊天消息支持 GitHub 风格 Markdown，包括代码块、表格、任务列表、删除线和行内代码。
- **丰富的会话元数据** — 显示会话 ID、创建时间、所属渠道、自定义标签和状态标记。
- **自定义标签系统** — 创建、保存并按用户自定义标签筛选会话，在"设置"中管理。
- **会话分页** — 首次加载 20 条会话，其余通过"加载更多"按需加载。
- **即时的乐观更新** — 状态、标记、标签、归档、重命名等操作立即响应，重载后仍然生效。

#### 渠道
- **重新设计的渠道页面** — 侧边栏 + 内容面板布局，按类别分组（办公、社交、国际），支持响应式折叠和完整键盘导航。
- **引导式设置向导** — 8 步模态向导，覆盖全部 9 个 IM 平台。
- **支持的 9 个平台：**
  - **办公（中国）：** 飞书、企业微信、钉钉
  - **社交（中国）：** 微信、QQ
  - **国际：** Telegram、Discord、Slack、WhatsApp

#### Agent 管理
- **完整的 Agent 管理面板** — 路由 Agent、健康检查、定时任务、活动日志等。
- **6 步 Agent 创建向导** — 用途 → 模板 → 配置 → 渠道 → 人格 → 部署。
- **每个 Agent 的专属配置：** 模型选择、人格编辑（8 个工作区 Markdown 文件）、工具策略、路由绑定、定时任务。
- **Gateway 健康面板** 带心跳配置。

#### 控制台
- **全新 Dashboard** — KPI 卡片、模型提供商卡片、快捷操作按钮。
- **Plugin Center** 显示已安装的 OpenClaw 插件。
- **Gateway 状态指示器** 在顶部显示降级状态消息。

#### 欢迎与环境检查
- **重新设计的欢迎页面** — 两列卡片布局，清晰说明 SetupClaw 的功能并引导新用户完成设置。
- **跳过已完成设置** — 应用记住已完成设置的用户，下次启动直接进入 Dashboard。
- **深度环境检查** — Node、Python、Git、OpenClaw CLI、Gateway、网络连接的全面验证，失败时提供可执行的修复建议。

#### 自动更新
- **通过 GitHub Releases 自动更新** — 已安装的 SetupClaw 会自动检测新版本并提示你。下载前通过 SHA-512 校验，所有构建均经过 Apple 签名并公证。
- **双语更新提示** — 更新对话遵循应用当前的语言设置。
- **手动下载回退** — 自动更新失败时，更新提示会显示直接下载链接。

#### 国际化
- **完整的英文和简体中文本地化** — 覆盖 16 个命名空间，200+ 个 Agent 相关翻译键。
- **Settings 中的语言切换器** — 即刻生效。

### 🐛 主要修复

- 修复聊天会话列表在慢速网络上闪烁空白。
- 修复首次启动的"白屏"问题。
- 修复右键菜单被背景遮挡的 z-index 问题。
- 修复重命名操作失去焦点。
- 修复 Mantine `Select` 在 `undefined` 数据时崩溃。
- 修复 Discord/QQ 渠道识别错误。
- 修复"在访达中显示"打开错误目录。
- 修复自动更新服务错误地报告"未配置"（当 publish provider 为 github 时）。

### 💾 系统要求

- **macOS:** 11 Big Sur 或更高版本。支持 Intel 和 Apple Silicon。
- **磁盘空间:** 约 400 MB，另需额外空间存放 OpenClaw 运行时和模型缓存。
- **网络:** 首次设置和自动更新检查需要网络连接。

### 📦 下载

[**SetupClaw-Lite.dmg**](https://github.com/maggielovelace/setupclaw-releases/releases/latest/download/SetupClaw-Lite.dmg) — 经过签名和公证的 macOS 安装包。
