# CLAUDE.md

## Project Overview

Programmatic Ad Studio — a Remotion-based video production engine that generates ad-grade promotional videos (promos, ads, presentations, social variants). Output quality bar: content that blends into Meta/TikTok/YouTube ad feeds and feels cinematic, not like animated slides.

Long-term goal: every asset and architecture decision must support future SaaS productization.

## Tech Stack

- **Video engine:** Remotion (React-based programmatic video)
- **Voice generation:** Gemini LLM/TTS pipeline
- **Workflow:** Terminal-first with Codex/Claude Code
- **Platform:** Node.js/TypeScript ecosystem

## Architecture Principles

- **Data + Template + Manifest** — every video is a typed render recipe, not a one-off script.
- **Modular components** — scenes, blocks, transitions, audio behaviors are independent, composable units.
- **Typed contracts** — template interfaces must be typed and versioned.
- **Parameterized over hardcoded** — prefer config-driven systems. No per-video hardcoding.
- **Render manifests** — every render saves its recipe (template version, inputs, assets, settings) for reproducibility.

## Pipeline (per video job)

1. Ingest brief (offer, audience, platform, tone, duration).
2. Generate script variants (hook/body/CTA).
3. Generate VO via Gemini + capture timing/transcript metadata.
4. Map script + assets into Remotion template.
5. Apply pacing, motion, typography, and audio quality checks.
6. Render platform variants.
7. Store manifest.

## Quality Rules (Always Enforce)

### Motion
- Custom easing curves. Never default ease-in-out everywhere.
- Motion hierarchy: primary (scene-defining), secondary (supporting), micro (liveliness).
- Depth via parallax layers.
- Seamless transitions (match cut, zoom-through, masked wipe, motion-matched exit). Fade-only = failure.
- Camera movement must have narrative purpose (push-in=emphasis, pull-out=reveal, parallax=depth/premium).

### Pacing
- Default structure: Hook 0-3s → Context 3-8s → Value 8-15s → Proof 15-20s → CTA final 3-5s.
- Cut on beats/emphasis. Sync text reveals to VO stress points. No dead frames.
- Flat pacing = presentation tier = must revise.

### Audio
- Audio is 50% of perceived quality — treat it accordingly.
- VO ducking over music (sidechain behavior).
- LUFS normalization per platform.
- No hard audio cuts. Keep ambient bed when scenes would feel empty.
- Emotional ramp in final 20%.

### Typography
- Max 2-3 font weights per template.
- Consistent type scale ratio.
- Word-level animation only when justified.
- Prefer mask reveals, clipping slides, blur-in accents.
- Never animate whole paragraphs as one block.

### Visual Consistency
- Consistent corner radius system, shadow/glow logic, brand tokens.
- Color temperature harmony. No random gradients or effects.

### Platform
- Respect 9:16 safe zones and UI occlusion.
- Reserve caption-safe space.
- Hook must be readable in silent autoplay.
- Handle dynamic crop variants. Select deliberate thumbnail frame.

## Zoom Standards

**Allowed:** micro push (3-6% over 2-4s), beat zoom (105-112% snap <200ms, sparingly), layered parallax.

**Disallowed:** constant zoom every scene, default zoom+fade combo, random rotation, fast snap without motion blur, zoom on elements already carrying heavy motion.

## Code Conventions

- Prefer TypeScript for all source files.
- Keep Remotion compositions as thin orchestrators — logic lives in hooks and utilities.
- Name scenes descriptively (e.g., `HookScene`, `ValueProposition`, `CTAScene`).
- Group by feature: each template gets its own directory with scenes, assets, and config.
- Export typed `InputProps` for every composition.
- Keep animation utilities (easing functions, spring configs, transition helpers) in a shared library.

## When Making Decisions

- Quality over speed when tradeoff is unavoidable.
- Fewer, stronger visual ideas over many weak effects.
- Simplify and increase intentionality when in doubt.
- Reject "good enough" slide-like motion.
- Every decision should be explainable and repeatable.

## Ship Gate Checklist

Before any video is considered done:
- [ ] Passes all quality sections in AGENTS.md
- [ ] Audio mix clean and normalized
- [ ] Typography and visual tokens consistent
- [ ] Pacing follows story rhythm, no dead air
- [ ] Hook strong in first 3 seconds
- [ ] CTA explicit and high-clarity
- [ ] Render manifest stored for reuse
