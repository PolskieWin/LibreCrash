# LibreCrash

> Lightweight, client-side Minecraft mod crash report and bytecode analyzer.

LibreCrash is a zero-dependency, single-file diagnostic web application designed to analyze Minecraft mod crash reports, `latest.log`, and JVM `hs_err_pid` dumps. It runs entirely inside your browser with no network transmission or external trackers.

---

## Features

- **Multi-Loader Detection:** Automatically identifies **Fabric**, **Quilt**, **NeoForge**, **Forge**, and Vanilla environments along with active Minecraft versions.
- **Java & Bytecode Diagnostics:** Exact detection for `UnsupportedClassVersionError` across major Java versions:
  - `61.0` &rarr; JDK 17 (Minecraft 1.18 – 1.20.4)
  - `65.0` &rarr; JDK 21 (Minecraft 1.20.5 – 1.21.11)
  - `69.0` &rarr; JDK 25 (Minecraft 26.1 – 26.4+)
- **Mobile Launcher Support:** Detects Android environments (**Libre Launcher**, **PojavLauncher**, **Amethyst**) and diagnoses mobile-specific GPU driver issues (Mesa Turnip, Zink, GL4ES) and Android Low Memory Killer (LMK) aborts.
- **Actionable Rule Engine:** Identifies:
  - Mixin injection conflicts (parsing failing configs and target classes)
  - Missing mandatory mod dependencies and version mismatches
  - Wrong loader jars (e.g. Forge mods dropped into Fabric folders)
  - Conflicting duplicate mod IDs
  - Memory exhaustion (heap `-Xmx` adjustments & mobile RAM slider recommendations)
  - Graphics pipeline faults (OpenGL, GLFW, Vulkan)
  - Deepest root-cause stacktrace extraction for unhandled crashes
- **Privacy Redaction Engine:** One-click redaction of local filesystem paths (`/storage/emulated/0/...`, `/home/...`, `C:\Users\...`), session tokens, UUIDs, and IPv4 addresses before generating shareable Markdown reports.
- **In-Memory GZIP Decompression:** Upload or drag-and-drop `.log`, `.txt`, or compressed `.gz` logs directly without manual extraction.
- **Sample Crashes Included:** Built-in test buttons for quick diagnostics testing.

---

## Getting Started

### Option 1: Browser (Direct File)
Simply open `index.html` in any modern web browser. No web server, Node.js, or build step required.

### Option 2: Local HTTP Server
Run a local static file server using Python:

```bash
python3 -m http.server 8080
```

Then visit `http://localhost:8080` in your browser.

---

## Privacy & Security

LibreCrash performs all parsing, regex evaluation, and log sanitization locally on your device via client-side JavaScript. No log data or telemetry is ever transmitted over the network.

---

## License

[MIT License](LICENSE) &copy; 2026 PolskieWin
