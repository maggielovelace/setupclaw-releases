# SetupClaw Releases

Official downloads for **SetupClaw**, the desktop setup wizard and management UI for OpenClaw.

> Source code lives in a private repository. This repo contains only binary releases, changelog, and issue tracking for download/install/update problems.

**Website:** https://setupclaw.uk — [English](https://setupclaw.uk/en/app) · [中文](https://setupclaw.uk/zh/app)

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
