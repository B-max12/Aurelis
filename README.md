<div align="center">
  <img src="public/icons/logo-mark-dark.png" alt="Aurelis Logo" width="128" height="128" />
  <h1>Aurelis</h1>
  <p><strong>Downloads, refined.</strong></p>
  <p>A modern, privacy-first, local-first download manager engineered with Tauri 2, React, TypeScript, and Rust.</p>
</div>

---

## ✦ Core Philosophy

- **Zero Telemetry Guarantee**: No tracking, no phone-home pings, no analytics, no external third-party calls. Ever.
- **Local-First Reliability**: Complete offline-first state persistence in SQLite with Write-Ahead Logging (WAL) and strict ACID durability.
- **Refined Aesthetics**: Thoughtful, calm, dark-first UI crafted with custom HSL design tokens, micro-interactions, responsive typography, and curated palettes (*Aureate, Celadon, Fjord, Dusk*).
- **High-Performance Rust Core**: Multi-connection streaming engine, atomic `.aurelis.part` writes, checksum verification (SHA-256, SHA-1, MD5), and dynamic speed throttling.

---

## ✦ Features

- **Multi-Part & Resumable Downloads**: Chunk-based streaming with automatic HTTP range resume and atomic finalization.
- **Dynamic Bandwidth Limiter**: Throttling controls that keep your network responsive during heavy downloads.
- **Intelligent Category Organization**: Automatic detection and destination routing for Archives, Audio, Documents, Images, Software, and Video.
- **Checksum Verification**: On-the-fly and post-download hash validation (SHA-256, SHA-1, MD5) with visual status indicators.
- **Command Palette & Keyboard First**: Global hotkey navigation (`Ctrl+K` / `Cmd+K`, `Ctrl+N` / `Cmd+N`, `Space`, `Delete`, `?`).
- **Configurable App Shell**: Customizable sidebar collapse, compact density, proxy support (HTTP & SOCKS5), custom user agents, and exportable JSON settings.

---

## ✦ Architecture

```text
Aurelis/
├── src/                          # Frontend Application
│   ├── components/               # Atomic UI components, domain cards & dialogs
│   │   ├── common/               # App layout, header, metric cards, command palette
│   │   ├── dialogs/              # Add download modal, confirmation dialogs
│   │   ├── downloads/            # Download rows, cards, badges, progress bars
│   │   └── ui/                   # Accessible shadcn-style primitives
│   ├── hooks/                    # Custom hooks (downloads, queue, settings, theme)
│   ├── pages/                    # Overview, Downloads, Queue, Completed, Failed, Settings, Stats
│   ├── services/                 # Tauri IPC invocations, web fallback, settings persistence
│   ├── stores/                   # Reactive state stores (Zustand)
│   ├── styles/                   # Design tokens (tokens.css) & global utilities (globals.css)
│   └── utils/                    # Validators, byte & speed formatters
├── src-tauri/                    # Rust Desktop Core
│   ├── migrations/               # Versioned SQLite migrations (001_initial, 002_indexes, 003_settings)
│   ├── src/
│   │   ├── commands/             # Typed Tauri 2 IPC commands (downloads, settings, system)
│   │   ├── database/             # SQLite connection pool (WAL), models, repository
│   │   ├── downloader/           # Streaming download engine, progress tracking, task manager
│   │   ├── errors/               # Domain errors & normalized error codes
│   │   ├── filesystem/           # Path sanitization, atomic .part file handling, disk checks
│   │   ├── network/              # Range requests, proxy configuration, URL validation
│   │   ├── settings/             # Settings manager & schema synchronization
│   │   └── lib.rs                # App entrypoint and IPC handler registry
└── public/icons/                 # Official light & dark brand assets
```

---

## ✦ Getting Started

### Prerequisites

- **Node.js**: >= 20
- **pnpm**: >= 9
- **Rust**: >= 1.77 (`rustup`)
- **Platform Dependencies**: Standard Tauri 2 dependencies (`libwebkit2gtk-4.1-dev`, `build-essential`, `curl`, `wget`, `file`, `libxdo-dev`, `libssl-dev`, `libayatana-appindicator3-dev`, `librsvg2-dev` on Linux)

### Installation

```bash
# Clone and enter the repository
cd Aurelis

# Install Node dependencies
pnpm install

# Run frontend preview dev server
pnpm dev

# Run unit tests
pnpm test

# Build production bundle
pnpm build
```

### Desktop Application

```bash
# Run full desktop app in development
pnpm tauri dev

# Run Rust engine tests
cd src-tauri && cargo test
```

---

## ✦ Keyboard Shortcuts

| Shortcut | Action |
| --- | --- |
| `Ctrl+N` / `Cmd+N` | Open Add Download Dialog |
| `Ctrl+K` / `Cmd+K` | Open Command Palette / Quick Search |
| `Space` | Pause or Resume Selected Download |
| `Delete` / `Backspace` | Remove Selected Download |
| `Ctrl+,` / `Cmd+,` | Navigate to Settings |
| `?` | Show Keyboard Shortcuts Help |

---

## ✦ Privacy Pledge

Aurelis is engineered with zero telemetry.
- No network requests are made other than the URLs you explicitly download.
- All download metadata, history, and preferences remain local in your SQLite database.
- Settings exports and imports are plain JSON files stored on your local drive.

---

## ✦ License

MIT License. See [LICENSE](LICENSE) for details.
