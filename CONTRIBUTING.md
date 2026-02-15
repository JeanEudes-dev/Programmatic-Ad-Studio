# Contributing to Programmatic Ad Studio

Thanks for your interest in contributing! This project is early stage, which means your contributions will have outsized impact on the direction and quality of the tool.

## Who Can Contribute

We welcome contributors with backgrounds in:

- **Frontend / React development** — Remotion compositions, components, animations
- **Motion design** — easing systems, transition design, cinematic motion patterns
- **Audio engineering** — ducking, normalization, layering, mix automation
- **TypeScript / Node.js** — pipeline tooling, CLI, type systems
- **AI / LLM integration** — script generation, TTS pipelines
- **Design systems** — typography scales, visual tokens, brand consistency

No contribution is too small. Documentation fixes, bug reports, and design feedback are all valuable.

## Getting Started

### 1. Fork and Clone

```bash
git clone https://github.com/<your-username>/Programmatic-Ad-Studio.git
cd Programmatic-Ad-Studio
npm install
```

### 2. Create a Branch

```bash
git checkout -b feature/your-feature-name
```

Branch naming conventions:
- `feature/` — new functionality
- `fix/` — bug fixes
- `refactor/` — code restructuring
- `docs/` — documentation changes
- `animation/` — motion/animation work
- `audio/` — audio system work

### 3. Make Your Changes

Before writing code, read:
- **[AGENTS.md](AGENTS.md)** — the full quality standard. Every contribution must meet these rules.
- **[CLAUDE.md](CLAUDE.md)** — architecture principles and code conventions.

### 4. Test Your Work

```bash
# Preview in Remotion studio
npm run dev

# Type check
npm run typecheck

# Lint
npm run lint
```

### 5. Submit a Pull Request

Push your branch and open a PR against `main`. In your PR description:
- Describe what you changed and why.
- Reference any related issue.
- Include a screen recording or screenshot if your change is visual.
- Confirm your change passes the quality checklist below.

## Code Standards

### TypeScript
- All source files must be TypeScript.
- Export typed `InputProps` for every Remotion composition.
- No `any` types unless absolutely unavoidable (and commented why).

### Remotion Conventions
- Compositions are thin orchestrators — logic lives in hooks and utilities.
- Name scenes descriptively: `HookScene`, `ValueProposition`, `CTAScene`.
- Each template gets its own directory with scenes, config, and assets.

### Animation
- Use shared animation utilities from `src/animations/`.
- Custom easing curves only — no default ease-in-out.
- Follow the motion hierarchy: primary, secondary, micro.

### File Organization
- Group by feature, not by type.
- Keep components colocated with the template that uses them.
- Shared utilities go in the appropriate `src/` subdirectory.

## Quality Checklist

Before submitting, verify:

- [ ] Motion uses custom easing (no default ease-in-out)
- [ ] No fade-only transitions
- [ ] Typography follows the type scale and weight limits
- [ ] Audio changes include proper ducking and normalization
- [ ] Visual tokens (colors, radii, shadows) are consistent
- [ ] Platform safe zones are respected for platform-specific work
- [ ] TypeScript compiles with no errors
- [ ] Code follows existing patterns in the codebase

## Issue Guidelines

### Reporting Bugs
- Use the **Bug Report** issue template.
- Include steps to reproduce, expected behavior, and actual behavior.
- Attach screenshots or recordings when possible.

### Requesting Features
- Use the **Feature Request** issue template.
- Describe the problem your feature solves.
- Explain how it fits the project's quality standards.

### Good First Issues
Look for issues tagged [`good first issue`](https://github.com/JeanEudes-dev/Programmatic-Ad-Studio/labels/good%20first%20issue). These are scoped, well-described tasks ideal for new contributors.

## Pull Request Process

1. PRs are reviewed for both code quality and adherence to [AGENTS.md](AGENTS.md) standards.
2. Visual changes require a screen recording or before/after screenshots.
3. Reviewers may request changes — this is normal and collaborative, not adversarial.
4. Once approved, a maintainer will merge your PR.

## Commit Messages

Use clear, descriptive commit messages:

```
feat: add kinetic typography mask-reveal component
fix: correct audio ducking timing during VO segments
refactor: extract easing utilities into shared library
docs: update roadmap with TTS integration milestone
```

Format: `type: description`

Types: `feat`, `fix`, `refactor`, `docs`, `style`, `test`, `chore`

## Questions?

Open a [discussion](https://github.com/JeanEudes-dev/Programmatic-Ad-Studio/issues) or comment on any issue. We're friendly and responsive.
