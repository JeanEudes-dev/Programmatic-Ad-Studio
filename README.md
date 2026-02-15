<p align="center">
  <h1 align="center">Programmatic Ad Studio</h1>
  <p align="center">
    <strong>Ad-grade video generation powered by LLMs + Remotion.</strong><br/>
    No templates. No drag-and-drop. Just code, structured specs, and cinematic output.
  </p>
</p>

<p align="center">
  <a href="LICENSE"><img alt="License: MIT" src="https://img.shields.io/badge/License-MIT-blue.svg"/></a>
  <a href="https://github.com/JeanEudes-dev/Programmatic-Ad-Studio/issues"><img alt="Issues" src="https://img.shields.io/github/issues/JeanEudes-dev/Programmatic-Ad-Studio"/></a>
  <a href="https://github.com/JeanEudes-dev/Programmatic-Ad-Studio/pulls"><img alt="PRs Welcome" src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg"/></a>
  <a href="CONTRIBUTING.md"><img alt="Contributors" src="https://img.shields.io/badge/contributions-welcome-orange.svg"/></a>
</p>

---

## What Is This?

Programmatic Ad Studio is an open-source engine that generates **production-quality promotional videos** — the kind you see in Meta, TikTok, and YouTube ad feeds — entirely from code and structured data.

Every video is defined as **data + template + render manifest**. You describe *what* you want (offer, audience, platform, tone), and the engine handles script generation, voice synthesis, cinematic motion, and multi-platform rendering.

**The quality bar:** every output should feel intentional and cinematic, never like animated slides. If a startup founder wouldn't pay $1k for it, it's not done.

## Why This Exists

Most programmatic video tools produce mediocre output — generic transitions, flat pacing, no audio craft. They're fine for volume, terrible for conversion.

This project proves that **code-driven video can match agency quality** by enforcing cinematic motion systems, structured story pacing, professional audio layering, and platform-aware rendering — all as reproducible, version-controlled pipelines.

## Architecture

```
Brief (JSON)          Script Generation         Voice Synthesis
+--------------+      +------------------+      +----------------+
| offer        | ---> | hook / body / CTA| ---> | Gemini TTS     |
| audience     |      | variant generation|      | timing metadata|
| platform     |      +------------------+      +----------------+
| tone         |                                        |
+--------------+                                        v
                                               Template Mapping
                                               +----------------+
                                               | Remotion scene |
                                               | composition    |
                                               | + motion system|
                                               | + audio layer  |
                                               +----------------+
                                                        |
                                                        v
                                               Quality Checks
                                               +----------------+
                                               | pacing         |
                                               | motion         |
                                               | typography     |
                                               | audio levels   |
                                               +----------------+
                                                        |
                                                        v
                                               Platform Renders
                                               +----------------+
                                               | 9:16 / 16:9    |
                                               | safe zones     |
                                               | LUFS per target|
                                               +----------------+
                                                        |
                                                        v
                                               Render Manifest
                                               +----------------+
                                               | template ver   |
                                               | inputs / assets|
                                               | settings       |
                                               +----------------+
```

## Tech Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| Video engine | [Remotion](https://www.remotion.dev/) | React-based programmatic video rendering |
| Voice generation | Gemini LLM/TTS | Script-to-speech with timing metadata |
| Language | TypeScript | Type-safe templates and pipeline logic |
| Runtime | Node.js | Build tooling and CLI pipeline |
| AI agents | Claude / Codex | Script generation, spec structuring |

## Project Status

> **Early stage** — architecture and quality standards are defined, core implementation is underway.

This is a ground-floor opportunity to shape a novel open-source tool. We're building in public and contributions at every level are welcome.

### Roadmap

- [x] Define quality standards and production rules ([AGENTS.md](AGENTS.md))
- [x] Define architecture principles and code conventions ([CLAUDE.md](CLAUDE.md))
- [ ] Scaffold Remotion project with TypeScript config
- [ ] Build shared animation utility library (easing, springs, transitions)
- [ ] Create first template: SaaS product promo (30s)
- [ ] Implement Gemini TTS integration with timing extraction
- [ ] Build brief-to-script generation pipeline
- [ ] Implement audio layering system (ducking, normalization, ambient beds)
- [ ] Build kinetic typography component library
- [ ] Create platform-aware rendering presets (Meta, TikTok, YouTube)
- [ ] Implement render manifest storage
- [ ] Build CLI for end-to-end video generation

## Getting Started

### Prerequisites

- **Node.js** >= 18
- **npm** or **pnpm**
- A **Gemini API key** (for voice generation)

### Setup

```bash
# Clone the repository
git clone https://github.com/JeanEudes-dev/Programmatic-Ad-Studio.git
cd Programmatic-Ad-Studio

# Install dependencies
npm install

# Start Remotion preview
npm run dev
```

> Setup instructions will be expanded as the project scaffolding is built.

## Project Structure (Planned)

```
Programmatic-Ad-Studio/
├── src/
│   ├── compositions/        # Remotion compositions (entry points)
│   ├── templates/           # Video templates (each with scenes, config, assets)
│   │   └── saas-promo/
│   │       ├── scenes/      # HookScene, ValueScene, CTAScene, etc.
│   │       ├── config.ts    # Template input props and defaults
│   │       └── index.tsx    # Template composition
│   ├── components/          # Shared visual components
│   ├── animations/          # Easing curves, springs, transition helpers
│   ├── audio/               # Audio utilities (ducking, normalization, layering)
│   ├── typography/          # Kinetic type components and presets
│   ├── pipeline/            # Brief ingestion, script gen, TTS, manifest
│   └── platform/            # Platform presets (safe zones, LUFS targets)
├── assets/                  # Shared static assets (fonts, SFX, ambient tracks)
├── briefs/                  # Example video briefs (JSON)
├── manifests/               # Stored render manifests
├── AGENTS.md                # Full production quality standards
├── CLAUDE.md                # AI agent working guidelines
├── CONTRIBUTING.md          # How to contribute
└── CODE_OF_CONDUCT.md       # Community standards
```

## Quality Standards

This project enforces a strict quality bar defined in [AGENTS.md](AGENTS.md). Every contribution is held to these standards:

| Domain | Key Rule |
|--------|----------|
| **Motion** | Custom easing, motion hierarchy (primary/secondary/micro), no fade-only composition |
| **Pacing** | Hook 0-3s, context 3-8s, value 8-15s, proof 15-20s, CTA final 3-5s |
| **Audio** | VO ducking, LUFS normalization, ambient beds, emotional ramp in final 20% |
| **Typography** | Max 2-3 weights, consistent scale, word-level animation only when justified |
| **Visuals** | Consistent tokens (radius, shadow, color), no random gradients or effects |
| **Platform** | 9:16 safe zones, caption space, silent autoplay readability |

Read the full spec: **[AGENTS.md](AGENTS.md)**

## Contributing

We welcome contributions from developers, motion designers, audio engineers, and anyone passionate about raising the bar for programmatic video.

See **[CONTRIBUTING.md](CONTRIBUTING.md)** for setup instructions, coding standards, and the PR process.

**Good first issues** are tagged with [`good first issue`](https://github.com/JeanEudes-dev/Programmatic-Ad-Studio/labels/good%20first%20issue).

## Community

- **Issues:** [GitHub Issues](https://github.com/JeanEudes-dev/Programmatic-Ad-Studio/issues) for bugs, features, and discussion
- **PRs:** [Pull Requests](https://github.com/JeanEudes-dev/Programmatic-Ad-Studio/pulls) always welcome

## License

This project is licensed under the **MIT License** — see [LICENSE](LICENSE) for details.

---

<p align="center">
  <sub>Built for creators who believe code can out-produce agencies.</sub>
</p>
