# 🎬 Fortify — AI Video Generation Prompt Pack

A complete brief for generating a **60–75 second cinematic launch trailer / explainer**
for the Fortify security skill. Built to work across modern AI video tools
(OpenAI Sora, Google Veo 3, Runway Gen-3/4, Kling, Pika, Luma Dream Machine) and
text-to-explainer tools (Synthesia, HeyGen, InVideo, Steve.ai).

> **How to use this:** Most AI video tools generate 5–10s clips. Generate each
> **SHOT** separately using its visual prompt, then assemble in order on a timeline
> and lay the **voiceover** + **music** over the top. If your tool takes one big
> box, paste the **§12 MEGA-PROMPT**. For talking-head/explainer tools, paste the
> **§5 VOICEOVER SCRIPT** as the narration and use §3 for the visual style.

---

## §1 · Logline & concept

> *A sleek, cinematic tech trailer that personifies "Fortify" as an intelligent
> shield: it scans a living 3D codebase, exposes glowing red vulnerabilities,
> seals them into protected green, then withstands a swarm of attacking drones —
> ending on a clean dashboard that flips from RED to GREEN.*

**Genre:** premium SaaS/dev-tool launch trailer (think Apple × Linear × a cyber
SOC). **Energy:** confident, precise, a little ominous in the middle (the threat),
triumphant at the end. **No humans required** — it's motion-graphics + 3D + UI.

## §2 · Technical spec

| Field | Value |
|---|---|
| Duration | 60–75 seconds |
| Aspect ratio | 16:9 master (also export 9:16 vertical + 1:1) |
| Resolution | 1920×1080 (4K if available) |
| Frame rate | 24 fps (cinematic) |
| Style | 3D + 2D motion graphics, UI/holographic overlays, no live actors |
| Pacing | ~10–12 shots, 4–8s each, beat-matched to music |

## §3 · Art direction (apply to every shot)

- **Mood:** dark, premium, high-contrast "security operations center" at night.
- **Color palette (use these hexes):**
  - Background: near-black navy `#0A0E1A` → deep indigo `#111A33`
  - Primary accent (Fortify / secure): electric cyan `#22D3EE` and teal `#2DD4BF`
  - "Secured / pass" state: neon green `#22C55E`
  - "Threat / vulnerability" state: alert red `#EF4444` + amber `#F59E0B`
  - Neutral text: soft white `#E5E7EB`
- **Lighting:** volumetric, rim-lit edges, subtle bloom/glow on accents, thin
  scan-line and grid textures, shallow depth of field, gentle film grain.
- **Typography:** bold geometric sans for headlines (Space Grotesk / Inter /
  Eurostile vibe); monospace (JetBrains Mono / IBM Plex Mono) for code & data.
- **Motion language:** smooth, weighted easing (no jitter); data assembles
  particle-by-particle; UI elements snap with crisp micro-interactions; camera
  moves are slow dollies, orbits, and push-ins — never shaky.
- **Recurring motif:** a faceted hexagonal **shield** made of glowing cyan
  circuitry; a padlock that "seals" with a ring of light; code that flows like a
  river of monospace glyphs.
- **Brand:** the word **Fortify** in white with a small cyan shield glyph 🛡; when
  shown, keep it centered and clean.

## §4 · Audio direction

- **Music:** cinematic electronic / hybrid trailer. Starts minimal (pulsing sub
  bass + ticking arpeggio), builds tension through the "attack" section, drops
  into a confident, melodic resolve at the green-dashboard finale. ~120–128 BPM.
- **SFX:** soft UI ticks/whooshes on text, a low "scan" sweep, a metallic
  "seal/lock" clunk-shimmer when vulns are fixed, deep impacts when drones hit the
  shield and bounce off, a bright rising chime on the final GREEN flip.
- **Voiceover:** one narrator. Profile: **calm, authoritative, modern** — a mix of
  a movie-trailer baritone and a confident product founder. Neither robotic nor
  hypey. Slight reverb, sits above the music. (For VO tools: "confident male or
  neutral, mid-30s, American, measured pace, cinematic.")

## §5 · Voiceover script (timed, ~150 words)

Read at a measured pace; pauses marked `(…)`.

```
[0:00] Every app ships with a question it can't answer…
[0:04] what's exposed — (…) and what happens when someone attacks it?
[0:09] Meet Fortify. A universal security skill that hardens any codebase —
       and then proves it.
[0:16] Point it at your project. It detects your stack and maps every door:
       what's open, what's locked… and to whom.
[0:24] Choose your level — from Basic, to Maximum.
[0:28] Fortify audits against the full attack catalog — injection, broken access
       control, secrets, supply chain, and more —
[0:36] mapped to OWASP, NIST, and SOC 2.
[0:40] It fixes what it finds. (…) Then comes the real test.
[0:45] A swarm of authorized agents attacks your hardened system.
[0:51] On the demo: ten vulnerabilities found… (…) and zero left standing.
[0:58] Every fix — verified. From red to green… automatically… on every commit.
[1:06] Fortify. (…) Security you can prove.
```

## §6 · On-screen data (use the REAL numbers)

- Findings on the vulnerable demo build: **10 total → 2 Critical · 5 High · 3 Medium**
- After hardening: **0 open** (all remediated & verified)
- Attack classes covered: **16** (injection, XSS, XXE, broken auth/JWT, access
  control/IDOR, SSRF, crypto, business logic, race/TOCTOU, supply chain, secrets,
  CI/CD, infra/cloud, DoS, mobile/desktop, APT)
- Tiers: **Basic → Standard → Hardened → Maximum**
- Compliance: **OWASP Top 10 · OWASP API Top 10 2023 · ASVS · NIST · CIS · SOC 2 · ISO 27001 · PCI-DSS**
- CI gate result: **PASSED** (fortify-scan · Semgrep · gate)
- Endpoints in demo: `POST /login`, `GET /search`, `GET /notes/:id`, `GET /admin/users`

---

## §7 · Shot-by-shot storyboard

> For each shot: paste **VISUAL PROMPT** into your video tool; overlay **ON-SCREEN
> TEXT**; align the matching **VO** line; apply **TRANSITION** into the next shot.

### SHOT 1 — Cold open: the dark codebase (0:00–0:04)
- **VISUAL PROMPT:** *Cinematic slow push-in through an infinite dark void of
  floating translucent code panels — monospace source code glowing faint cyan,
  drifting like a galaxy. Near-black navy background `#0A0E1A`, volumetric haze,
  shallow depth of field, subtle film grain, thin scan-lines. One question mark of
  light pulses softly in the center. Premium, ominous, high-contrast. 24fps,
  anamorphic, slow dolly forward.*
- **ON-SCREEN TEXT:** *(none, or a faint blinking cursor)*
- **VO:** "Every app ships with a question it can't answer…"
- **SFX:** low sub-bass swell + single UI tick. **TRANSITION:** push-through.

### SHOT 2 — The two questions (0:04–0:09)
- **VISUAL PROMPT:** *Two glowing holographic lines of text materialize
  particle-by-particle over the drifting code field, cyan glow, light bloom. A red
  ember flickers ominously behind the second line. Cinematic, dark, depth of
  field.*
- **ON-SCREEN TEXT:** Line 1: `WHAT'S EXPOSED?` Line 2 (tinted red): `WHAT IF SOMEONE ATTACKS?`
- **VO:** "what's exposed — and what happens when someone attacks it?"
- **TRANSITION:** light-streak wipe to black.

### SHOT 3 — Logo reveal (0:09–0:16)
- **VISUAL PROMPT:** *A faceted hexagonal shield of glowing cyan circuitry
  assembles from particles in the center of frame, emitting a soft shockwave of
  light that pushes the haze outward. Clean reflective floor with subtle grid.
  Heroic, premium, Apple-keynote lighting. Slow orbit around the shield.*
- **ON-SCREEN TEXT:** `🛡 FORTIFY` (white, centered) → subtitle fades in:
  `Harden any project. Then prove it.`
- **VO:** "Meet Fortify. A universal security skill that hardens any codebase — and then proves it."
- **SFX:** rising shimmer + soft impact on logo lock. **TRANSITION:** match-cut to UI.

### SHOT 4 — Detect the stack / map the doors (0:16–0:24)
- **VISUAL PROMPT:** *Top-down/iso view of a glowing 3D wireframe "building" made
  of code modules representing an app. A cyan scan-beam sweeps across it; little
  labeled doors light up on the surface — some glowing green (locked), some red
  (open). Holographic labels float: `/login`, `/search`, `/notes/:id`,
  `/admin/users`. Clean SOC aesthetic, volumetric light, slow orbit.*
- **ON-SCREEN TEXT:** `ACCESSIBILITY MAP — what's open vs. locked` ; small chips:
  `Web · API · Mobile · Desktop · auto-detected`
- **VO:** "Point it at your project. It detects your stack and maps every door: what's open, what's locked… and to whom."
- **TRANSITION:** UI slide-left.

### SHOT 5 — Choose your tier (0:24–0:28)
- **VISUAL PROMPT:** *Four sleek vertical pillars rise in sequence, each taller and
  brighter, glowing from green to cyan to amber to red-cyan. A selector glides
  across them. Holographic, dark stage, reflective floor.*
- **ON-SCREEN TEXT:** `BASIC → STANDARD → HARDENED → MAXIMUM`
- **VO:** "Choose your level — from Basic, to Maximum."
- **TRANSITION:** quick whoosh.

### SHOT 6 — The audit / attack catalog (0:28–0:40)
- **VISUAL PROMPT:** *A dense radial constellation of 16 glowing icon-nodes orbits
  the central shield — each node a tiny glyph (a syringe for injection, a key for
  auth, a broken lock for access control, a chain-link for supply chain, etc.).
  Scan lines connect them to the code building. As the camera pushes in, three
  compliance crests light up. Cinematic, intricate, cyan-on-navy with red accents.*
- **ON-SCREEN TEXT:** rotating tags: `Injection · XSS · IDOR · SSRF · Secrets ·
  Supply chain · Business logic · DoS …` then crest row: `OWASP · NIST · SOC 2`
- **VO:** "Fortify audits against the full attack catalog — injection, broken access control, secrets, supply chain, and more — mapped to OWASP, NIST, and SOC 2."
- **TRANSITION:** seal-flash to next.

### SHOT 7 — It fixes what it finds (0:40–0:45)
- **VISUAL PROMPT:** *Close-up: three red glowing vulnerability cracks across a
  pane of dark glass. A ring of cyan light sweeps over each crack and SEALS it —
  the red dissolves into solid neon green, a padlock icon clicks shut with a
  shimmer. Satisfying, tactile, macro lens, bokeh.*
- **ON-SCREEN TEXT:** small toasts: `SQLi → parameterized ✓`, `IDOR → ownership check ✓`, `SHA1 → argon2id ✓`
- **VO:** "It fixes what it finds. Then comes the real test."
- **SFX:** metallic seal-shimmer ×3. **TRANSITION:** hard cut on a bass hit.

### SHOT 8 — The red-team swarm attacks (0:45–0:51) — TENSION PEAK
- **VISUAL PROMPT:** *Epic wide shot: the glowing cyan hexagonal shield stands in a
  dark arena while dozens of small angular red drones/arrows swarm in from all
  directions and slam into it — each impact bursts into sparks and bounces off
  harmlessly, rippling the shield's hex pattern. Dramatic, dynamic, slow-motion
  impacts, volumetric smoke, red vs cyan. Camera orbits heroically.*
- **ON-SCREEN TEXT:** `AUTHORIZED RED-TEAM SWARM` · small label `localhost only · non-destructive`
- **VO:** "A swarm of authorized agents attacks your hardened system."
- **SFX:** rapid impacts, deep booms, shield resonance. **TRANSITION:** flash to data.

### SHOT 9 — The result: 10 → 0 (0:51–0:58) — DATA HERO SHOT
- **VISUAL PROMPT:** *A holographic dashboard assembles in mid-air. On the left, a
  bar chart and a pie chart glow RED/AMBER showing "10 findings: 2 Critical, 5
  High, 3 Medium." A sweep of cyan light passes left-to-right and the bars
  collapse to zero, recoloring to GREEN. A big number counts down 10 → 0. Clean
  data-viz, monospace labels, premium UI, subtle particle trails.*
- **ON-SCREEN TEXT:** `FOUND: 10` (red) → `REMAINING: 0` (green) · subtitle
  `2 Critical · 5 High · 3 Medium → 0`
- **VO:** "On the demo: ten vulnerabilities found… and zero left standing."
- **SFX:** descending tick as numbers fall + bright resolve chime. **TRANSITION:** UI push-in.

### SHOT 10 — Verified on every commit / CI green (0:58–1:06)
- **VISUAL PROMPT:** *A clean CI/CD pipeline UI: a row of check items flips one by
  one from a spinning state to green checkmarks — `fortify-scan ✓`, `Semgrep ✓`,
  `gate ✓` — and a status pill flips from red `FAILED` to green `PASSED`. Behind
  it, a git graph of commits each lights green. Crisp, modern devtool UI, glassy,
  cyan/green glow.*
- **ON-SCREEN TEXT:** `CI SECURITY GATE: PASSED` · `every PR · every commit`
- **VO:** "Every fix — verified. From red to green… automatically… on every commit."
- **SFX:** three crisp check ticks + success chime. **TRANSITION:** glow bloom to logo.

### SHOT 11 — End card / CTA (1:06–1:12)
- **VISUAL PROMPT:** *The hexagonal cyan shield returns, now calm and fully solid
  green-cyan, slowly rotating. Logo locks up centered. Background settles to deep
  navy with a faint grid and gentle particle drift. Premium, confident, still.*
- **ON-SCREEN TEXT:** `🛡 FORTIFY` · tagline `Security you can prove.` · small URL
  `github.com/mitulpatelp112-svg/cybersecurity-`
- **VO:** "Fortify. Security you can prove."
- **SFX:** final soft shimmer, music resolves. **TRANSITION:** slow fade to black.

---

## §8 · Lower-thirds / captions (optional burn-ins)
- `Universal security skill for Claude Code`
- `Audit · Harden · Red-team · Report`
- `Maps to OWASP · NIST · CIS · SOC 2 · ISO 27001 · PCI-DSS`
- `Localhost / authorized targets only — defensive by design`

## §9 · End-card details
- Primary: `🛡 FORTIFY — Security you can prove.`
- Secondary: `Works on web · API · mobile · desktop`
- Repo: `github.com/mitulpatelp112-svg/cybersecurity-`

## §10 · Negative prompt (paste into the "avoid" / negative field)
```
no real human faces, no actors, no hands typing, no stock-photo people,
no cartoonish or childish style, no cluttered messy UI, no unreadable tiny text,
no gibberish/garbled letters, no misspellings, no watermark, no logos of other
brands, no low resolution, no jitter or shaky cam, no motion blur smearing,
no oversaturated neon vomit, no horror/gore, no flashing strobe that could
trigger photosensitivity, no skulls/hacker-in-hoodie cliché, no green "Matrix"
falling-code cliché, no slow boring static shots
```

## §11 · Per-tool tips
- **Sora / Veo 3:** generate each shot from its §7 visual prompt; Veo can also do
  the SFX — append the shot's SFX line. Keep prompts to ~1 paragraph; lead with
  camera + subject + lighting.
- **Runway Gen-3/4:** use the visual prompt as the text prompt; add a first-frame
  image (render the on-screen text as a still) for clean typography, since video
  models garble text. **Best practice: add all on-screen text in post**, not via
  the model.
- **Kling / Pika / Luma:** shorter clips; split SHOT 6 and SHOT 9 into 2 sub-clips.
- **Synthesia / HeyGen / InVideo (explainer):** paste §5 as the script, pick a
  calm presenter or VO, and use §3 palette + §6 data for the slide visuals.
- **Universal:** render typography/charts as overlays in CapCut/Premiere/After
  Effects/DaVinci; AI video models should produce the *backgrounds and motion*,
  not the words.

---

## §12 · MEGA-PROMPT (single-box version)

> Paste this whole block into a tool that takes one prompt (then trim to your
> tool's character limit, keeping the first and last thirds):

```
A 70-second cinematic launch trailer for "Fortify", a universal cybersecurity tool
that hardens software and then attack-tests it. No humans — pure premium 3D motion
graphics and holographic UI, like an Apple keynote meets a high-end security
operations center at night. Visual style: near-black navy background (#0A0E1A),
electric cyan and teal accents (#22D3EE/#2DD4BF), neon green for "secured"
(#22C55E), alert red/amber for threats (#EF4444/#F59E0B); volumetric light, soft
bloom, thin scan-lines, fine film grain, shallow depth of field, slow weighted
camera dollies and orbits, 24fps anamorphic.

Sequence: (1) slow push-in through an infinite void of floating glowing
monospace-code panels with a pulsing question mark. (2) Two holographic lines
appear: "WHAT'S EXPOSED?" and, tinted red, "WHAT IF SOMEONE ATTACKS?". (3) A
faceted hexagonal shield of cyan circuitry assembles from particles and emits a
light shockwave — title "FORTIFY" locks center. (4) An isometric glowing wireframe
"app building" is scanned by a cyan beam; little doors light up green (locked) or
red (open) with floating API labels. (5) Four rising pillars: BASIC → STANDARD →
HARDENED → MAXIMUM. (6) A radial constellation of 16 glowing attack-type icons
orbits the shield; OWASP/NIST/SOC 2 crests light up. (7) Macro shot: red cracks in
dark glass are sealed by a ring of cyan light, turning solid green as a padlock
clicks shut. (8) Tension peak: dozens of small red drones swarm and slam into the
glowing shield in slow motion, bursting into sparks and bouncing off. (9) A
holographic dashboard shows a red chart "10 findings: 2 Critical, 5 High, 3
Medium"; a cyan sweep collapses every bar to zero and recolors green as a big
number counts 10 → 0. (10) A devtool CI pipeline flips checks to green
("fortify-scan ✓, Semgrep ✓, gate ✓") and a status pill flips red FAILED → green
PASSED. (11) End card: the calm green-cyan shield rotates slowly, "FORTIFY —
Security you can prove." centered on deep navy with faint grid and drifting
particles. Mood arc: ominous → heroic → tense → triumphant. Cinematic hybrid
electronic trailer music ~124 BPM, UI ticks, metallic seal-shimmers, deep impacts
on the shield, bright resolve chime at the end. Crisp, legible, premium, confident.
Avoid: real faces, hacker-in-hoodie and Matrix falling-code clichés, garbled text,
watermarks, shaky cam, strobing.
```

## §13 · Optional 15-second teaser (for ads / social)
- Use **SHOT 3 (logo)** → **SHOT 8 (swarm attack)** → **SHOT 9 (10→0)** →
  **SHOT 11 (end card)**.
- VO: *"Fortify hardens your code — then proves it. Ten vulnerabilities found.
  Zero left standing. Security you can prove."*
- 9:16 vertical, punchy cut on each beat.
