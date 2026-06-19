# T1NK3R-V3R53 // UNI-STALLER

Universal sovereign software installer for the T1NK3R-V3R53 ecosystem. Built with Tauri v2 (Rust + vanilla JS). Generates ready-to-run bootstrap scripts for any OS from one interface — no cloud, no telemetry, offline capable.

## What it does

- **10 OS tabs** — Tiny11/Windows, CachyOS, Bazzite, Fedora, Ubuntu/Debian (+ Ubuntu Studio), Arch, macOS, iPadOS, Android
- **JUMPSTART God Mode** — curated "arm all" bootstrap block per OS: base tools, runtimes (nvm/Rust/pipx), Ollama, companions
- **Companion Models** — canonical T1NK3R-V3R53 roster pre-populated: Alfred (qwen2.5:14b), Sage (gemma2:9b), Scout (mistral-nemo), Spark (llama3.2:3b), Coach + Solace (llama3.1:8b), Steward + Wren (mistral:7b), Daisy (phi3:mini), Luna (llama3.2:latest)
- **Script generator** — outputs `.ps1` (Windows) or `.sh` (Linux/macOS) from your selections, deduped and ordered correctly
- **OpenRouter importer** — writes your OR key to the correct OS-specific path, generates setup script
- **ROCm support** — AMD RX 6600 / RDNA2 paths on CachyOS, Bazzite, Fedora, Ubuntu, Arch
- **Cross-OS mode** — use any tab from any OS; cross-platform warning banners activate automatically
- **Native Tauri execution** — when running as a built app, scripts can execute directly with live terminal output
- **Ubuntu Studio detection** — auto-routes to Ubuntu tab from both Tauri native (`/etc/os-release` `ID=ubuntu-studio`) and JS hash (`#ubuntu-studio`)

## Stack

```
src/
  index.html       — 10 OS tab structure, OpenRouter panel, header
  app.js           — all data (JUMPSTART + CATS), state, generators (3000+ lines)
  styles.css       — T1NK3R-V3R53 dark theme, OS color vars
  tauri-bridge.js  — Tauri v2 ↔ browser fallback bridge, terminal output

src-tauri/
  src/lib.rs       — Rust: detect_platform(), detect_pkg_managers(), run_install(), save_script()
  Cargo.toml       — tauri v2, shell, dialog, fs, os, notification plugins
  tauri.conf.json  — window config (1280×900), identifier com.tinkerverse.uni-staller
```

## Build

Requires Rust + Cargo and Node.js.

```bash
# Install Tauri CLI (one-time)
cargo install tauri-cli --version "^2"

# Dev server
cargo tauri dev

# Production build
cargo tauri build
```

Output binaries land in `src-tauri/target/release/bundle/`.

## Calsifer (second machine)

```bash
cd ~/Uni-staller
cargo tauri build
```

Tauri CLI v2.11.3 was compiled via `cargo install` on Calsifer/Ubuntu Studio. Use `cargo tauri build` for production bundles.

## Part of T1NK3R-V3R53

- GitHub org: [Tinker-AI-Labs](https://github.com/Tinker-AI-Labs)
- License: GPL v3
- Companion to: Alfred, Ollama, TinkerOS, the SR32 Corridor sovereign stack
