# Changelog

## v1.9.26 (2026-03-11) — 🔧 Fix Auto-Scroll Not Reaching Last Button

- 🐛 **Fix auto-scroll missing buttons** — When multiple command runs were present, auto-scroll only scrolled a nested code output container instead of the main conversation scroll
- 🔄 **Scroll all containers** — `findDeepestScrollable()` → `findAllScrollables()` — scrolls ALL scrollable containers simultaneously instead of only the deepest one
- 📁 **File:** `compositor.js` (autoScroll function)

## v1.9.25 (2026-03-02) — 🗑️ Remove Telegram Dead Code

- 🗑️ **Removed all Telegram code** — require, variables, globalState init, bridge start, command registrations, 4 functions (~120 lines)
- 🗑️ **Deleted `telegram-bridge.js`** — file no longer needed
- 🧹 **Clean logs** — No more `[Telegram] Configured/Starting/Bridge started` spam

## v1.9.24 (2026-03-02) — 📋 Unified Click Log

- 📋 **Always-on click log** — Rejected buttons with reasons logged to History & Data (no toggle needed)
- 🔄 **Dedup** — Consecutive identical rejects grouped with ×N count badge instead of spamming
- 🔍 **Filter buttons** — All / ✅ Clicks / ⚠️ Rejected filter tabs in History section
- 🗑️ **Removed Diagnostic Mode toggle** — No longer needed, tracking is always-on with zero overhead
- 🎨 **History UI** — 3 color-coded types: ✅ accept (green), ⚠️ reject (yellow), 🚫 block (red)

## v1.9.23 (2026-03-02) — 🚨 Hotfix: Missing Brace Regression

- 🐛 **Fix v1.9.22 regression** — Missing `}` closing brace in `else` block of `findButton()` caused syntax error in generated permission script → ALL click patterns stopped working
- 🔧 **1-character fix** — Added missing `}` that was lost when wrapping diag code in `if(DIAG_MODE){}`

## v1.9.22 (2026-03-02) — 🔍 Diagnostic Mode Toggle

- 🔍 **Diagnostic Mode toggle** — Settings Panel → Advanced → ON/OFF switch to enable `diag:{}` logging
- 🧹 **Zero overhead when OFF** — All diagnostic tracking code wrapped in `DIAG_MODE` conditional
- ⚙️ **Persisted via globalState** — Toggle survives IDE restarts
- 📡 **HTTP Live Sync** — Diagnostic mode exposed to compositor via HTTP config endpoint

## v1.9.21 (2026-03-02) — ✅ Accept All Definitive Fix

- 🎯 **`closestClickable()` depth 5→10** — Accept All text in `<strong>` tag nested deep under `<button>` — now traverses 10 levels to find clickable parent
- ✅ **`isApprovalDialog()` accept whitelist** — Buttons with text containing "accept" bypass reject-sibling requirement (Accept All appears standalone in Antigravity)
- 📊 **Diagnosed via `diag:{}`** — `not-clickable:strong` and `approval-guard` rejection codes pinpointed exact root causes

## v1.9.20 (2026-03-02) — Overlay Fix + CDP Timeout

- 🚫 **Removed `overlay` from blocklists** — Both `isApprovalDialog()` and `isInsideDropdownOrMenu()` incorrectly blocked buttons in overlay-classed containers
- ⏱️ **CDP `_evaluate` timeout 2s→5s** — 30KB compositor script failed injection on complex workspace pages

## v1.9.19 (2026-03-01) — Deep Diagnostic

- 🔍 **`diag:{}` return codes** — Permission script returns JSON with rejection reasons: `approval-guard`, `not-clickable:<tag>`, `zero-size`
- 📊 **`[CDP-Perm-DIAG]` logging** — All non-null results logged to Output channel for debugging

## v1.9.18 (2026-03-01) — Anti-Spam CDP Dialog

- 🔕 **`cdp-offline-notified` flag** — CDP offline dialog shows only once per offline transition
- 🔄 **Auto-reset** — Flag resets when CDP comes back online, re-enabling the dialog for future outages

## v1.9.17 (2026-03-01) — CDP Setup Dialog Restored

- ⚠️ **Actionable dialog when CDP offline** — Shows "Auto-Fix CDP" + "Setup Guide" buttons even when `cdpSetupDone=true`
- 🔧 **Replaced silent status bar** — Previously only showed status bar warning after first setup, now shows dialog

## v1.9.16 (2026-03-01) — e.isTrusted Fix

- 🔒 **`e.isTrusted` guard** — Keystroke listener only tracks real user keydown events, ignoring synthetic events from agent text generation
- 🐛 **Fixed perpetual typing guard** — Agent writing code dispatched synthetic keystrokes → typing guard stayed active forever → no buttons clicked

## v1.9.15 (2026-03-01) — Diagnostic Build

- 🔍 Diagnostic logging + `e.isTrusted` check added to trace Accept All behavior (temporary)

## v1.9.14 (2026-03-01) — 3 Bug Fixes

- 🐛 **`isBackgroundMode` reference error** — Dead code from v1.8.8 BG removal crashed extension startup
- 🔧 **Health check null** — `evaluateOnAllPages` too strict filter skipped valid results
- 📊 **False click counting** — `checkPermissionButtons` counted non-click results as clicks

## v1.9.13 (2026-03-01) — Debug: User Click Capture

- 🔍 **User click capture** — Added click event listener logging to identify exactly which buttons users interact with and which layer rejects them

## v1.9.12 (2026-03-01) — Debug: Targeted Reject Logging

- 🔍 **Reject logging** — Each compositor layer now logs WHY it rejected a button (tag, role, dropdown ancestor, text mismatch)

## v1.9.11 (2026-03-01) — ✅ Accept All Fix: startsWith

- 🎯 **startsWith for ≥5 char patterns** — `"accept all"` now matches `"accept all changes"` via `startsWith` instead of exact `===`
- 🔒 **Exact match for <5 chars** — Short patterns like `"run"` still use exact match to prevent `/run` false positives
- 🧹 **Cleaned DIAG logging** — Removed leftover diagnostic logging from v1.9.8

## v1.9.10 (2026-03-01) — ✅ Accept All Regression Fix

- 🔄 **Tiered `isApprovalDialog()`** — 3-tier logic: (1) reject sibling → allow all, (2) `<button>` not in dropdown → allow, (3) non-button → block
- 🐛 **Fix v1.9.9 regression** — `cursor-pointer` bypass removal was too aggressive, blocking all standalone `<button>` elements

## v1.9.9 (2026-03-01) — ✅ Real Fix: CDP Permission Script

- 🔍 **Root cause found** — Slash command false clicks came from `buildPermissionScript()` in `extension.js`, NOT from `compositor.js`. Two click systems run in parallel; only compositor was being fixed (v1.9.2-v1.9.7)
- 🎧 **Keystroke listener installed** — `__lastKeystrokeTime` was checked but never set → typing guard was always bypassed
- ⏱️ **Slash/mention 5s debounce** — Same protection added to CDP Permission script
- 🚫 **Removed `cursor-pointer` bypass** — `isApprovalDialog()` no longer auto-approves elements with `cursor-pointer` class. Now requires actual reject sibling button

## v1.9.8 (2026-03-01) — Diagnostic Build

- 🔍 DOM diagnostic logging added to identify false click source (temporary, removed in v1.9.9+)

## v1.9.7 (2026-03-01) — Event-Based Typing Guard + Floating Overlay Detection

- 🎧 **Keydown event listener** — Real-time detection of `/` and `@` keystrokes with 5-second debounce (was: 2s polling that lost track when focus left input)
- 🎯 **Floating overlay detection** — Checks if clicked element is inside a `position:absolute/fixed` container (catches unknown dropdown classes), with workbench panel exclusions
- 🔒 **Root cause fixed** — Slash command dropdown click was caused by focus leaving input → old polling returned false → extension clicked item

## v1.9.6 (2026-03-01) — Structural Button Detection

- 🛡️ **4-layer whitelist** — Completely redesigned click detection: tag validation → role exclusion → per-element dropdown ancestor check → exact text match
- 🎯 **Per-element ancestor check** — walks 15 parent levels checking 14 class patterns + 5 ARIA roles to detect dropdowns, menus, popups, and suggestion widgets
- ✅ **Exact text match** — `/run` no longer matches `run` pattern (was substring match, now exact)
- 🏷️ **Tag validation** — only clicks `<button>`, `<a>`, or `[role=button]` elements, not `<div>`/`<li>`/`<span>`
- 🔒 **Fixes slash command and @mention false clicks** — dropdown items are rejected at 3 independent layers

## v1.9.5 (2026-03-01) — Streamlined Click Patterns

- 🎯 **10 essential patterns** — Reduced from 24 to 10 focused defaults: Run, Accept, Accept all, Allow, Always Allow, Keep Waiting, Retry, Continue, Allow Once, Allow This Con
- 🔄 **Force reset for all users** — All existing users get patterns overwritten to the new clean defaults
- 🗑️ **Removed**: Run All, Run Command, Apply, Execute, Confirm, Proceed, Yes, Ok, Save, Approve, Enable, Install, Update, Overwrite

## v1.9.4 (2026-03-01) — Auto-Merge Click Patterns

- 🔄 **Auto-merge new defaults** — Existing users automatically receive new click patterns on extension update without losing their custom settings

## v1.9.3 (2026-03-01) — Unified Click Patterns

- 🔗 **24 unified patterns** — Synced DEFAULT_PATTERNS across `extension.js`, `settings-panel.js`, `compositor.js` — all 3 sources now identical
- ➕ **New patterns**: Run, Apply, Execute, Confirm, Allow Once, Allow This Con, Proceed, Continue, Yes, OK, Save, Approve, Keep Waiting, Enable, Install, Update, Overwrite

## v1.9.2 (2026-03-01) — 3-Layer Slash Protection

- 🛡️ **Widget detection** — `isSuggestionWidgetVisible()` checks for suggestion overlays before clicking
- 🎭 **Role exclusion** — `isAcceptButton()` skips elements with `role=option/listbox/menuitem`
- 🔽 **Dropdown guard** — `clickAlwaysRunDropdown()` skips when suggestion widget is visible

## v1.9.1 (2026-03-01) — README Rewrite

- 📝 **Local README** — Concise with GitHub distribution link
- 🌍 **Distribution README** — 4-language (EN/VI/ZH/JA) marketing copy with version badges

## v1.9.0 (2026-03-01) — Status Bar Redesign & Typing Guard

- 🎨 **Status bar redesign** — Full name "Agent Auto Approve", hover tooltip with Turn ON/OFF + Settings links
- 🔘 **Panel ON/OFF toggle** — Prominent switch at settings panel header with green/red indicator
- ⌨️ **Typing Guard** — Pauses auto-click when user types `/` (slash commands) or `@` (mentions) in chat input, 2s grace period
- 📊 **Incremental stats refresh** — Stats update every 5s via `postMessage` without re-rendering HTML, preserves collapse state
- 🏷️ **Lifetime chip** — Lifetime stats badge in dashboard

## v1.8.15 (2026-03-01) — Defaults Button Fix

- 🔧 **Factory reset** — "Defaults" button now resets to factory `DEFAULT_PATTERNS` (including Accept pattern)

## v1.8.14 (2026-03-01) — WebView Escaping Fix

- 🐛 **Restore `\\n` escaping** — Fixed all buttons broken since v1.8.12 by restoring double-escaped newlines in WebView `<script>` templates

## v1.8.13 (2026-03-01) — JS Escaping Fix

- 🐛 **Fix broken JS escaping** — Settings panel buttons and toggles now work correctly after escaping regression

## v1.8.12 (2026-03-01) — Emoji Fix

- 🐛 **Fix emoji display** — Replace double-escaped unicode (`\\uXXXX` text) with actual emoji characters in settings panel

## v1.8.11 (2026-03-01) — Settings Panel Redesign

- ✨ **Glassmorphism design** — Modern frosted-glass settings panel
- 🔀 **Toggle switches** — Replace checkboxes with smooth toggle switches
- 🎚️ **Range sliders** — For frequency and scroll config
- 🍞 **Toast feedback** — Non-intrusive save confirmations
- 🐛 **Fix banned commands bug** — Banned commands now load from storage on activation
- 🕐 **Local time in history** — Session history shows local timestamps

## v1.8.10 (2026-03-01) — Feature Cleanup

- 📝 **README rewrite** — Status bar tooltip guide, removed outdated commands reference

## v1.8.9 (2026-03-01) — Dead Code Removal

- 🗑️ **Delete `auto_accept.js`** — Removed dead legacy code
- 🔧 **Fix click patterns** — Corrected pattern matching
- 🗑️ **Remove `autoFixCDP` redundancy** — Consolidated with existing setup flow

## v1.8.8 (2026-02-28) — Current Conversation Only

- 🗑️ **Removed Background Mode entirely** — Tab cycling interrupted user input
- 🎯 **Current conversation only** — Extension accepts on visible conversation, user switches manually
- 🗑️ **Removed**: BG toggle, lock file, BG status bar badge, compositor BG script loading, `hideBackgroundOverlay()`

## v1.8.7 (2026-02-28) — Fix BG Infinite Loop

- 🐛 **Remove `antigravityLoop()` new-conversation click** — Was creating infinite conversations every 6s
- ⏱️ **Idle backoff** — Poll interval increases from 3s to 10s when no activity
- 🔒 **Tabs > 1 guard** — Tab cycling only when multiple tabs exist

## v1.8.6 (2026-02-28) — Remove Overlay

- 🗑️ **Overlay removed completely** — Background overlay was blocking agent panel, status bar tooltip is sufficient

## v1.8.5 (2026-02-28) — Compact Overlay

- 📐 **Compact mini-overlay** — Smaller overlay that no longer blocks agent panel

## v1.8.4 (2026-02-28) — Scan-First Shortcut Discovery

- 🔍 **Scan-first approach** — Scans ALL `.lnk` files in 4 locations (User Start Menu, Public Start Menu, Desktop, TaskBar), matches by TargetPath regex instead of hardcoded filenames
- 🎯 **Zero hardcoded names** — Uses `IDE_EXE_PATTERN` regex (`antigravity|cursor|windsurf|trae|code`) on TargetPath. Works regardless of shortcut filename
- 📂 **Recursive Start Menu** — Scans subfolders (e.g. `Programs\Antigravity\`, `Programs\Visual Studio Code\`) 1 level deep
- 🆕 **`_collectLnkFiles()`** — Efficient .lnk file collector with optional recursive scan

## v1.8.1 (2026-02-28) — README Rewrite

- 📝 **Marketing-focused README** — Compelling copy, value proposition table, cleaner feature descriptions, removed external links

## v1.8.0 (2026-02-28) — Shared i18n Module

- 🌐 **Unified i18n system** — Single `i18n.js` module for all translations (settings panel + dialogs + status bar)
- 🗑️ **Removed 270 lines** of inline i18n from settings-panel.js
- 🌍 **All dialogs localized** — Welcome, CDP setup, offline warning, error messages now follow language setting (EN/VI/ZH/JA)
- 📦 **Single source of truth** — Change a translation once, updates everywhere

## v1.7.8 (2026-02-28) — English-Only Dialogs

- 🌐 **All dialogs now in English** — Welcome message, CDP setup prompt, CDP offline warning, status bar tooltip, and error messages all translated from Vietnamese to English

## v1.7.7 (2026-02-28) — Changelog Cleanup

- 📝 **English-only changelog** — Removed all non-English text, consolidated minor version entries, removed external repo references

## v1.7.6 (2026-02-28) — Background Mode Default ON

- 🔄 **Background mode ON by default** — Multi-tab cycling now works out of the box, zero config needed. Toggle still available in Safety & Advanced section.

## v1.7.5 (2026-02-28) — Fix Runtime Errors

- 🐛 **Fix 132 uncaught errors** — Removed dead references to `commandPollTimer`/`startCommandPolling`/`stopCommandPolling` (leftover from native polling removed in v1.7.0)

## v1.7.4 (2026-02-28) — Settings Panel Cleanup

- 🗑️ **Removed Telegram** — Entire Telegram integration removed from settings panel (HTML, i18n, JS handlers, export/import)
- 🔇 **Hidden BG badge** — Background mode badge no longer shown in status badges
- 📂 **Safety & Advanced collapsed** — Section now collapsed by default, less overwhelming for new users
- 🧹 **Cleaned tooltip** — Status bar tooltip no longer shows Background/Telegram status

## v1.7.3 (2026-02-28) — Fix All Shortcuts + Smart Popup

- 🔧 **Modify ALL shortcuts** — Start Menu, Desktop, AND Taskbar pinned icon all get CDP flag
- 🔇 **Smart popup suppress** — After first successful setup, CDP-offline events show silent status bar warning
- 🔔 **Modal Setup Dialog** — Setup popup now uses `modal: true`, bypasses Do Not Disturb mode
- 📌 **Persistent Status Bar Warning** — Warning stays visible when user postpones, click to re-trigger
- ⚙️ **CDP Status in Settings** — Shows Active/Offline banner with 1-click setup button (i18n: EN/VI/ZH/JA)

## v1.7.1 (2026-02-27) — Zero-Config Auto-Setup

- 🚀 **Auto-Setup CDP** — Extension auto-prompts "Setup & Restart" when CDP is not enabled — 1 click, 1 time only
- 🌍 **Cross-Platform Support** — Windows (.lnk modify), macOS (wrapper script), Linux (.desktop modify)
- 🔄 **IDE Update Recovery** — Auto-detects CDP lost after IDE update, prompts 1-click fix
- 🔧 **New `relauncher.js`** — Complete rewrite of cross-platform relaunch mechanism

## v1.7.0 (2026-02-27) — 100% CDP Architecture

- 🏗️ **Removed native command polling entirely** — definitive slash command fix:
  - Root cause: `executeCommand()` fired blindly every 1s → intercepted slash commands
  - Extension now 100% CDP-only — no `executeCommand()` calls for accept/run/allow
- 🗑️ **Removed**: `ACCEPT_COMMANDS`, `PATTERN_COMMAND_MAP`, `startCommandPolling()`, `discoverCommands()`, keyboard fallback
- ⚠️ **Requires CDP**: `--remote-debugging-port=9222` flag needed for auto-accept functionality

## v1.6.0–v1.6.1 (2026-02-27) — Zero-Config UX

- 🎉 **Zero-Config Install** — Extension works immediately, no CDP setup required
- ⚡ **Native Commands First** — Uses IDE-native accept/run commands as primary method
- 🔄 **Pattern → Command Mapping** — Click patterns map to specific native commands
- 🏥 **Health Check System** — Monitors CDP connection, auto-degrades gracefully
- 🔍 **Auto-Discovery** — Finds new IDE accept commands every 5 minutes

## v1.5.0–v1.5.3 (2026-02-27) — Resilience & Control

- 🎯 **Approval dialog detection** — Only clicks elements inside real approval dialogs (checks for sibling Reject/Deny/Cancel buttons)
- 🎛️ **Pattern-Mapped Commands** — Disable "Run" → `terminalCommand.run` stops firing
- ⚡ **Health Check** — CDP monitored every 30s, auto-degrades after 3 failures, auto-recovers
- 🔄 **Command Discovery** — Rediscovers IDE commands every 5 minutes
- 🛡️ **Dropdown detection** — Structural fix for slash/mention conflict using ancestor role checks

## v1.4.0–v1.4.6 (2026-02-27) — Settings Refactor & Slash Fix

- ✨ **Settings Panel Refactor** — Complete overhaul of settings UI
- 🎯 **Click patterns** — 3-column grid with instant-save toggles + custom patterns
- 🔀 **Merged Safety + Advanced** sections into single collapsible section
- ⚡ **Smart typing debounce** — Pauses auto-clicking during active typing (1.5s cooldown)
- 📊 **Stats count-up animation** — Smooth count-up with easing
- ➕ **5 new patterns**: Accept, Enable, Install, Update, Overwrite
- 📊 **Fix stats real-time display** — Delta-based stats collection with live status bar updates

## v1.3.0–v1.3.1 (2026-02-27) — Status Bar & Safety

- 📊 **Status bar accept count** with rich tooltip
- 🛡️ **Fix false clicks** on workflow suggestions and @mentions
- 🚫 **Input area exclusion** — Skip buttons inside textarea, input, contenteditable
- 🏷️ **Button tag validation** — Only click `<button>`, `<a>`, `[role=button]`
- 📐 **Minimum size check** — Buttons must be ≥20×12px

## v1.2.0–v1.2.9 (2026-02-27) — UI Polish & Branding

- 🎨 **Redesigned status bar** — Single smart item with rich tooltip, dynamic badges
- 🌐 **i18n support** (EN/VI/ZH/JA) for entire settings panel
- 🏷️ **Agent Approve branding** throughout
- 🔖 **Smart dynamic badges** (ON/OFF/Schedule) in status bar
- 📡 **Telegram Bot Integration** — Remote monitoring and control (removed in v1.7.4)

## v1.1.0 (2026-02-27) — Core Rewrite

- 🔧 **Complete rewrite** of `auto_accept.js` — Clean, modular, auditable code
- ✨ `expandCollapsedSections()` — Auto-expand hidden steps requiring input
- ✨ `clickAlwaysRunDropdown()` — Auto-click "Always run" in permission dropdowns
- 🛡️ Improved `isInConversationArea()` — Exclusion-first strategy to prevent false positives

## v1.0.0 (2026-02-27) — Initial Release

- 🎉 **Agent Auto Approve** — Auto-click configurable patterns (Allow, Continue, Retry, etc.)
- 🔄 **Background Mode** — Multi-tab CDP cycling
- 📜 **Auto Scroll** — Smart chat panel detection
- 🔒 **Safe Click & Diff Protection**
- 🧠 **Smart Accept** — Blocks dangerous commands
- 📡 **HTTP Live Sync** — Real-time settings push
- ⏰ **Auto-Schedule & Smart Frequency**
- 📊 **ROI Dashboard** with session history
