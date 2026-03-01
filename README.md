# ⚡ Agent Auto Approve

[![Version](https://img.shields.io/badge/version-1.9.24-brightgreen)](https://open-vsx.org/extension/hasugoii/agent-auto-approve) [![Open VSX](https://img.shields.io/badge/Open%20VSX-Install-blue)](https://open-vsx.org/extension/hasugoii/agent-auto-approve) [![Antigravity](https://img.shields.io/badge/IDE-Antigravity-black)](https://www.antigravity.dev)

**[English](#english) · [Tiếng Việt](#tiếng-việt) · [中文](#中文) · [日本語](#日本語)**

---

<a id="english"></a>

## 🇬🇧 English

> **Stop babysitting your AI agent.** Let it code while you grab coffee.

Every time your AI agent asks — **Accept**, **Allow**, **Run**, **Continue** — this extension clicks it for you. Instantly. Safely. While you sleep.

### 📥 Install

**From Open VSX (Recommended):**

1. Open **Antigravity IDE** → **Extensions** (`Ctrl+Shift+X`)
2. Search **"Agent Auto Approve"**
3. Click **Install**

> Or [download the latest .vsix](../../releases) → Command Palette → "Install from VSIX"

### 🚀 3 Steps to Start

1. **`Ctrl+Shift+A`** to enable
2. **Click "Setup & Restart"** when prompted *(one-time)*
3. ☕ Go grab coffee. Your agent runs uninterrupted.

### ✨ Features

- 🎯 **Auto-Click** — Accept, Allow, Run, Continue, Retry, Keep Waiting...
- 🛡️ **Smart Safety** — Blocks `rm -rf`, `format c:`, `dd` and dangerous commands
- 🔒 **Safe Click** — Only clicks real dialogs (verifies sibling Reject/Cancel)
- 🚫 **Diff Protection** — Won't click "Accept Changes" in merge editor
- ⌨️ **Typing Guard** — Pauses when you type `/` or `@` (dropdown stays open)
- 📜 **Auto Scroll** — Follows conversation, pauses when you scroll up
- ⏰ **Schedule** — Auto-activate during your working hours
- 📊 **Dashboard** — Track clicks, blocked commands, time saved
- 🌍 **4 Languages** — English · Tiếng Việt · 中文 · 日本語

### 🔧 After IDE Updates

CDP may reset. The extension auto-detects and shows a fix prompt — click **"Setup & Restart"**.

---

<a id="tiếng-việt"></a>

## 🇻🇳 Tiếng Việt

> **Ngừng trông chừng AI agent.** Để nó code, còn bạn đi pha cà phê.

Mỗi khi AI agent hỏi — **Accept**, **Allow**, **Run**, **Continue** — extension này tự click giúp bạn. Ngay lập tức. An toàn. Kể cả lúc bạn ngủ.

### 📥 Cài đặt

**Từ Open VSX (Khuyên dùng):**

1. Mở **Antigravity IDE** → **Extensions** (`Ctrl+Shift+X`)
2. Tìm **"Agent Auto Approve"**
3. Nhấn **Install**

> Hoặc [tải file .vsix mới nhất](../../releases) → Command Palette → "Install from VSIX"

### 🚀 3 Bước để bắt đầu

1. **`Ctrl+Shift+A`** để bật
2. **Nhấn "Setup & Restart"** khi được hỏi *(chỉ 1 lần)*
3. ☕ Đi pha cà phê. Agent chạy tự do.

### ✨ Tính năng

- 🎯 **Tự động click** — Accept, Allow, Run, Continue, Retry, Keep Waiting...
- 🛡️ **Bảo vệ thông minh** — Chặn `rm -rf`, `format c:`, `dd` và các lệnh nguy hiểm
- 🔒 **Click an toàn** — Chỉ click dialog thật (kiểm tra có nút Reject/Cancel bên cạnh)
- 🚫 **Bảo vệ Diff** — Không click "Accept Changes" trong merge editor
- ⌨️ **Bảo vệ gõ phím** — Tạm dừng khi bạn gõ `/` hoặc `@` (dropdown vẫn hiện)
- 📜 **Tự cuộn** — Theo dõi cuộc hội thoại, dừng khi bạn cuộn lên đọc
- ⏰ **Lịch trình** — Tự bật/tắt theo giờ làm việc
- 📊 **Dashboard** — Theo dõi số click, lệnh bị chặn, thời gian tiết kiệm
- 🌍 **4 Ngôn ngữ** — English · Tiếng Việt · 中文 · 日本語

### 🔧 Sau khi cập nhật IDE

CDP có thể bị reset. Extension sẽ tự phát hiện — nhấn **"Setup & Restart"** để sửa.

---

<a id="中文"></a>

## 🇨🇳 中文

> **别再盯着 AI agent 了。** 让它写代码，你去喝咖啡。

每次 AI agent 询问 — **Accept**、**Allow**、**Run**、**Continue** — 这个扩展会自动帮你点击。即时。安全。即使你在睡觉。

### 📥 安装

**从 Open VSX（推荐）：**

1. 打开 **Antigravity IDE** → **扩展** (`Ctrl+Shift+X`)
2. 搜索 **"Agent Auto Approve"**
3. 点击 **安装**

> 或 [下载最新 .vsix 文件](../../releases) → 命令面板 → "Install from VSIX"

### 🚀 3 步开始

1. **`Ctrl+Shift+A`** 启用
2. 提示时 **点击 "Setup & Restart"** *（仅一次）*
3. ☕ 去喝杯咖啡。Agent 不间断运行。

### ✨ 功能

- 🎯 **自动点击** — Accept、Allow、Run、Continue、Retry、Keep Waiting...
- 🛡️ **智能安全** — 阻止 `rm -rf`、`format c:`、`dd` 等危险命令
- 🔒 **安全点击** — 仅点击真实对话框（验证旁边有 Reject/Cancel 按钮）
- 🚫 **Diff 保护** — 不会点击合并编辑器中的 "Accept Changes"
- ⌨️ **输入保护** — 输入 `/` 或 `@` 时暂停（下拉建议保持打开）
- 📜 **自动滚动** — 跟踪对话，向上滚动时暂停
- ⏰ **定时计划** — 按工作时间自动启用/禁用
- 📊 **仪表盘** — 跟踪点击数、被阻止的命令、节省的时间
- 🌍 **4 种语言** — English · Tiếng Việt · 中文 · 日本語

### 🔧 IDE 更新后

CDP 可能重置。扩展自动检测 — 点击 **"Setup & Restart"** 修复。

---

<a id="日本語"></a>

## 🇯🇵 日本語

> **AIエージェントの監視をやめましょう。** コーディングは任せて、コーヒーを飲みに行こう。

AIエージェントが確認を求めるたび — **Accept**、**Allow**、**Run**、**Continue** — この拡張機能が自動でクリックします。即座に。安全に。あなたが寝ている間も。

### 📥 インストール

**Open VSXから（推奨）：**

1. **Antigravity IDE** → **拡張機能** (`Ctrl+Shift+X`) を開く
2. **"Agent Auto Approve"** を検索
3. **インストール** をクリック

> または [最新の .vsix をダウンロード](../../releases) → コマンドパレット → "Install from VSIX"

### 🚀 3ステップで開始

1. **`Ctrl+Shift+A`** で有効化
2. プロンプトが表示されたら **"Setup & Restart"** をクリック *（初回のみ）*
3. ☕ コーヒーを飲みに行こう。エージェントは中断なく動作。

### ✨ 機能

- 🎯 **自動クリック** — Accept、Allow、Run、Continue、Retry、Keep Waiting...
- 🛡️ **スマート安全機能** — `rm -rf`、`format c:`、`dd` などの危険なコマンドをブロック
- 🔒 **安全クリック** — 実際のダイアログのみクリック（Reject/Cancelボタンの存在を確認）
- 🚫 **Diff保護** — マージエディタの "Accept Changes" をクリックしない
- ⌨️ **入力ガード** — `/` や `@` 入力時は一時停止（ドロップダウン候補を保持）
- 📜 **自動スクロール** — 会話を追跡、上にスクロールすると一時停止
- ⏰ **スケジュール** — 勤務時間に自動で有効化/無効化
- 📊 **ダッシュボード** — クリック数、ブロックされたコマンド、節約時間を追跡
- 🌍 **4言語** — English · Tiếng Việt · 中文 · 日本語

### 🔧 IDEアップデート後

CDPがリセットされる場合があります。拡張機能が自動検出 — **"Setup & Restart"** をクリックして修復。

---

**Made with ⚡ by [hasugoii](https://github.com/hasugoii)**
