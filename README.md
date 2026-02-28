# ⚡ Agent Auto Approve — for Antigravity IDE

> **Stop babysitting your AI agent.** Let it code while you grab coffee.

Every time your AI agent asks for permission — **Accept**, **Allow**, **Run**, **Continue** — this extension clicks it for you. Instantly. Automatically. Safely.

---

## 📥 Install

### Option 1: From Open VSX (Recommended)

[![Install from Open VSX](https://img.shields.io/badge/Install-Open%20VSX-blue?logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZD0iTTEyIDJMMyAxMmw5IDEwIDktMTBMMTIgMnoiIGZpbGw9IndoaXRlIi8+PC9zdmc+)](https://open-vsx.org/extension/hasugoii/agent-auto-approve)

1. Open **Antigravity IDE**
2. Go to **Extensions** panel (`Ctrl+Shift+X`)
3. Search **"Agent Auto Approve"**
4. Click **Install**

### Option 2: Manual VSIX Install

1. Download the latest `.vsix` from [Releases](../../releases)
2. In Antigravity, open Command Palette (`Ctrl+Shift+P`)
3. Type **"Install from VSIX"**
4. Select the downloaded file

---

## 🚀 Quick Start

1. **Press `Ctrl+Shift+A`** to enable
2. **Click "Setup & Restart"** when prompted (one-time setup)
3. **Done.** Your agent now runs uninterrupted.

---

## ✨ Features

- 🎯 **Auto-Click** — Accept, Allow, Run, Continue, Retry, Keep Waiting...
- 🛡️ **Smart Safety** — Blocks `rm -rf`, `format`, `dd` and other dangerous commands
- 🔒 **Safe Click** — Only clicks real dialogs (verifies sibling Reject/Cancel button)
- 🚫 **Diff Protection** — Won't click "Accept Changes" in merge/diff editor
- ⌨️ **Typing Guard** — Pauses when you type `/` or `@` to preserve dropdown suggestions
- 📜 **Auto Scroll** — Follows the conversation, pauses when you scroll up
- ⏰ **Auto-Schedule** — Set working hours for automatic activation
- 📊 **ROI Dashboard** — Track clicks saved, commands blocked, time saved
- 🌍 **4 Languages** — English · Tiếng Việt · 中文 · 日本語
- ⚙️ **Customizable Patterns** — Add/remove click patterns from Settings

---

## 🔧 After IDE Updates

IDE updates may reset the CDP connection. The extension **auto-detects** this and shows a fix prompt — just click **"Setup & Restart"**.

---

## 📋 Changelog

See [CHANGELOG.md](./CHANGELOG.md) for full version history.

---

**Made with ⚡ by [hasugoii](https://github.com/hasugoii)**
