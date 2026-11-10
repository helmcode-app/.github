<div align="center">

  <img src="https://helmcode-app.github.io/assets/images/icon.png" alt="HelmCode Logo" width="96" height="96" style="border-radius: 22px; box-shadow: 0 8px 24px rgba(0,0,0,0.35);" />

  # HelmCode

  ### Mobile-First iPad AI Coding Console

  <p align="center">
    A professional, distraction-free AI coding environment built exclusively for iPad.<br>
    Pure native SwiftUI ergonomics, offline CodeMirror 6 editor, multi-model ACP Agent Commander, and self-hosted WebSocket VFS.
  </p>

  <p align="center">
    <a href="https://helmcode-app.github.io"><img src="https://img.shields.io/badge/Website-helmcode--app.github.io-06b6d4?style=flat-square&logo=googlechrome&logoColor=white" alt="Website" /></a>
    <img src="https://img.shields.io/badge/Platform-iPadOS%20Only-3b82f6?style=flat-square&logo=apple&logoColor=white" alt="Platform: iPadOS Only" />
    <img src="https://img.shields.io/badge/Architecture-Self--Hosted-10b981?style=flat-square&logo=docker&logoColor=white" alt="Self-Hosted" />
    <img src="https://img.shields.io/badge/Protocol-ACP%20Harnesses-8b5cf6?style=flat-square&logo=anthropic&logoColor=white" alt="ACP Harnesses" />
    <a href="https://github.com/helmcode-app/HelmCode/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-f59e0b?style=flat-square" alt="MIT License" /></a>
  </p>

  <br />

  <a href="https://helmcode-app.github.io">
    <img src="https://helmcode-app.github.io/assets/images/hero-screenshot.png" alt="HelmCode iPad Interface" width="880" style="border-radius: 14px; box-shadow: 0 16px 40px rgba(0,0,0,0.5);" />
  </a>

</div>

---

### ⚡ Overview

**HelmCode** transforms the iPad into a genuine, desktop-grade software engineering workstation. By decoupling pure-native iPadOS UI rendering from backend execution, you get fluid multi-column navigation and millisecond-level editing on the device, while heavy compiler toolchains, Git trees, and AI model dispatches run securely on your self-hosted daemon.

> **Platform Scope**: HelmCode is engineered **exclusively for iPad (iPadOS)** to take full advantage of large-canvas touch interaction, multi-column `NavigationSplitView`, and hardware keyboards. iOS (iPhone) and macOS are not currently supported.

---

### 🧩 Core Repositories

| Repository | Description | Key Technologies |
| :--- | :--- | :--- |
| **[`HelmCode`](https://github.com/helmcode-app/HelmCode)** | The native iPad client shell | Swift, SwiftUI, CodeMirror 6, xterm.js WebSSH |
| **[`runner-core`](https://github.com/helmcode-app/runner-core)** | Headless sandbox daemon & execution plane | Node.js open-core, Go `helm-vfs`, in-process PTY, ACP |
| **[`helmcode-app.github.io`](https://github.com/helmcode-app/helmcode-app.github.io)** | Official landing page & legal policies | Jekyll, GitHub Pages, SEO, Terms & Privacy |

---

### ✨ Highlights

- **Pure iPadOS SwiftUI Ergonomics**: Native split-view columns, custom project switcher, full touch gestures, and desktop keyboard shortcuts (`⌘O` Quick Open, `⌘P` Palette, `⌘J` Terminal toggle, `⌘S` Save).
- **CodeMirror 6 Offline Core**: Millisecond-level typing responsiveness with bundled syntax highlighters for Swift, TypeScript, Go, Python, Rust, Dockerfile, and more.
- **Agent Commander (ACP Protocol)**: Multi-model AI orchestration supporting OpenCode, Claude, Codex, Cursor, and Grok. Use `/skills` to trigger tasks and `@files` to anchor workspace context.
- **WebSocket Remote VFS**: High-speed JSON-RPC over WebSocket connects to `runner-core` for instant repo indexing, large-file chunk streaming, and live Git staging/diff inspection.
- **WebSSH Terminal (`⌘J`)**: Instant in-app PTY session powered by xterm.js for `npm build`, `cargo test`, Docker management, and shell scripting.
- **100% Self-Hosted & Private**: Device authentication tokens are secured in the Apple Keychain. Zero telemetry, zero cloud code interception, and zero proprietary analytics.

---

### 🏛️ System Architecture

```text
┌────────────────────────────────────────────────────────┐
│                   iPad Client                          │
│  NavigationSplitView  ·  CodeMirror 6  ·  Commander    │
└───────────────────────────┬────────────────────────────┘
                            │
               WebSocket / REST (Bearer Token)
                            │
┌───────────────────────────▼────────────────────────────┐
│              runner-core (Self-Hosted Daemon)          │
│  • Node.js Control Plane (/v1/sessions, /v1/vfs)       │
│  • Go helm-vfs (Fast Workspace & Git JSON-RPC)         │
│  • In-process PTY WebSSH Terminal Server               │
└───────────────────────────┬────────────────────────────┘
                            │
               ACP Protocol (stdio ndjson)
                            │
┌───────────────────────────▼────────────────────────────┐
│              AI Harnesses / ACP Servers                │
│    OpenCode  ·  Claude  ·  Codex  ·  Cursor  ·  Grok   │
└────────────────────────────────────────────────────────┘
```

---

### 🚀 Quick Start

#### 1. Launch `runner-core` on your server or workstation

Run the headless container with your workspace mounted:

```bash
docker run -d \
  -p 18080:8080 \
  -v $(pwd):/app/workspace \
  --name runner-core \
  helmcode/runner-core:latest
```

#### 2. Connect from HelmCode on iPad

1. Launch **HelmCode** on your iPad.
2. Tap **Add Runner** on the welcome page.
3. Enter your runner endpoint and the generated pairing code (e.g. `http://192.168.1.100:18080` with setup code `SDCN-9XZS`).
4. Select your Git repository and begin coding!

---

### 🌐 Official Links

- **Website**: [helmcode-app.github.io](https://helmcode-app.github.io)
- **Terms of Service**: [helmcode-app.github.io/terms](https://helmcode-app.github.io/terms/)
- **Privacy Policy**: [helmcode-app.github.io/privacy](https://helmcode-app.github.io/privacy/)
- **Report an Issue**: [github.com/helmcode-app/HelmCode/issues](https://github.com/helmcode-app/HelmCode/issues)

---

<p align="center">
  <sub>Built with ❤️ for mobile-first developers by the HelmCode Team. Licensed under the <a href="https://github.com/helmcode-app/HelmCode/blob/main/LICENSE">MIT License</a>.</sub>
</p>
