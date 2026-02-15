# AGENTS.md

## Mission
Build ad-grade promotional videos that can stand next to Apple, Google, or Stripe campaign content. Output must feel intentional, cinematic, and conversion-focused, not like animated slides.

This repository is a long-term content engine. Every asset and workflow decision must preserve reuse for future SaaS productization.

## Operating Context
- Primary operator: terminal-first workflow with Codex.
- Video engine: Remotion.
- Voice generation: Gemini LLM/TTS pipeline.
- Typical outputs: promo, ads, presentations, social variants.

## Non-Negotiable Quality Bar
Before shipping any video, pass all checks:
1. Would this blend naturally into a Meta/TikTok/YouTube ad feed?
2. Would a startup founder pay $1k for this video?
3. Does it feel intentional instead of "AI animated"?

If any answer is no, revise.

## Core Production Rules

### 1) Cinematic Motion System (Required)
- Use custom easing curves. Avoid default ease-in-out everywhere.
- Enforce motion hierarchy:
  - Primary motion: scene-defining movement.
  - Secondary motion: supporting movement.
  - Micro motion: tiny feedback/liveliness.
- Use depth with subtle parallax layers.
- Include micro-interactions where relevant (tap pulse, ripple, UI response).
- Prefer seamless transitions (match cut, motion-matched exits, zoom-through, masked wipes).
- Avoid fade-only composition. "Everything fades in" is a failure.

### 2) Structured Story Pacing (Required)
Default pacing model:
- 0-3s: Hook (pattern interrupt).
- 3-8s: Context/problem.
- 8-15s: Product/value.
- 15-20s: Proof/credibility.
- Final 3-5s: Strong CTA.

Pacing rules:
- Cut on beats or emphasis changes.
- Sync text reveals to VO stress points.
- Remove dead frames.
- Flat pacing equals presentation tier and must be revised.

### 3) Professional Audio Layering (Required)
- Apply VO ducking over music (sidechain style behavior).
- Normalize loudness (target LUFS per platform preset).
- No hard audio cuts between scenes.
- Keep low-level ambient bed when scenes would otherwise feel empty.
- Build emotional ramp in the final 20%.
- Treat audio as 50% of perceived quality.

### 4) Kinetic Typography System (Required)
- Max 2-3 font weights per template.
- Use consistent type scale ratio.
- Define emphasis rules (keywords, split lines, contrast words).
- Use word-level animation only when justified.
- Prefer mask reveals, clipping slides, blur-in accents.
- Never animate whole paragraphs as one block by default.

### 5) Visual Language Consistency (Required)
- Enforce consistent corner radius system.
- Enforce shadow/glow logic (no random effects).
- Enforce brand tokens (color, spacing, typography).
- Maintain color temperature harmony.
- Avoid random gradients.

### 6) Platform Intelligence (Required)
- Respect 9:16 safe zones and UI occlusion areas.
- Reserve caption-safe space.
- Ensure hook readability in silent autoplay.
- Handle dynamic crop variants safely.
- Select a deliberate thumbnail frame.

### 7) Subtle Cinematic Effects (Use Lightly)
- Light film grain only.
- Motion blur on fast movement and snap transitions.
- Soft bloom on highlights.
- Very subtle depth-of-field simulation.
- Slight camera push-in for static scenes.
- Overuse of any effect is a quality failure.

## Camera Language Rules
Never move camera without narrative reason.

Allowed intent mapping:
- Push-in: emphasis, intensity.
- Pull-out: reveal, perspective.
- Side pan: exploration/comparison.
- Parallax drift: depth, premium tone.
- Snap zoom: urgency, impact beat.

If movement has no narrative reason, remove it.

## Zoom Standards
### Allowed
- Micro push: 3-6% scale over 2-4s.
- Beat zoom: 105-112% snap under 200ms on key words/SFX (sparingly).
- Layered parallax: foreground/mid/background differential motion.

### Disallowed
- Constant zoom in every scene.
- Default zoom + fade combo everywhere.
- Random rotation.
- Fast snap zoom without motion blur.
- Zoom on elements already carrying heavy motion.

## Transition Standards
Prefer over basic fade:
- Match-position transitions.
- Mask wipes from UI geometry.
- Text transforming into next-scene shapes.
- Zoom-through transitions.
- Whip pan with controlled blur.

## Visual + Audio Coupling
For impact beats (when appropriate):
- Add soft impact SFX.
- Add subtle sub-bass pulse.
- Add micro shake (max ~2px).

Coupled cues are stronger than visual-only cues.

## Energy Curve Enforcement
Sequence energy by section:
1. Hook: aggressive.
2. Explanation: stable.
3. Demo/value: controlled movement.
4. CTA: focused intensity.

Enforce per scene:
- Max zoom percentage.
- Motion curve consistency.
- Energy level tag.

## Engine Architecture Directives
Build for reusable templates and future SaaS.
- Treat each video as data + template + render manifest.
- Keep template contracts typed and versioned.
- Store render recipes for reproducibility.
- Keep components modular (scenes, blocks, transitions, audio behaviors).
- Prefer parameterized systems over per-video hardcoding.

## Minimum Pipeline Per Video Job
1. Ingest brief (offer, audience, platform, tone, duration).
2. Generate script variants (hook/body/CTA).
3. Generate VO via Gemini and capture timing/transcript metadata.
4. Map script + assets into selected Remotion template.
5. Apply pacing, motion, typography, and audio quality checks.
6. Render platform variants.
7. Save manifest (template version, inputs, assets, settings).

## Definition of Done (Ship Gate)
A video is done only if:
- It passes all required sections in this file.
- Audio mix is clean and normalized.
- Typography and visual tokens are consistent.
- Pacing follows story rhythm with no dead air.
- Hook is strong in first 3 seconds.
- CTA is explicit and high-clarity.
- Render manifest is stored for future reuse.

## Behavior for Future Agents
- Prioritize quality over speed when tradeoff is unavoidable.
- Reject "good enough" slide-like motion.
- Prefer fewer, stronger visual ideas over many weak effects.
- Keep decisions explainable and repeatable.
- When in doubt, simplify and increase intentionality.
