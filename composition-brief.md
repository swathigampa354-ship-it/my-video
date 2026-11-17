# Hyperframes Composition Brief: TryPost

## Objective
Create a short launch-style brag video for TryPost (trypost.it) — the agentic social media scheduler.

## Output
- Composition directory: `~/brag-output/composition/`
- Rendered video: `~/brag-output/brag.mp4`
- Format: landscape — 1920x1080, 30fps
- Duration: 19 seconds

## Source Material
- Project root: remote website https://trypost.it/en (cached HTML at /data/data/com.termux/files/usr/tmp/opencode/trypost/index.html)
- Primary files read: site HTML (hero, live demo mocks, feature sections, FAQ), theme CSS variables
- Product name: TryPost
- Tagline / strongest claim: "Connect an agent over MCP. It plans, writes, and schedules a week of posts across every network." / "$19 a month with unlimited social accounts and team members"
- Key UI or visual moment to recreate: the dark chat-card demo (prompt → agent reply chip), the black-bordered content calendar on warm paper, the analytics stat cards
- Copy that must appear verbatim:
  - "Plan this weekend for my coffee shop."
  - "Writing captions and scheduling posts"
  - "Scheduled 3 posts to Instagram, TikTok, and X"
  - "Content calendar" / "3 scheduled"
  - "Happy hour: 2-for-1 coffees this Friday" (FRI · Instagram)
  - "Behind the scenes: roasting Saturday's beans" (SAT · TikTok)
  - "Weekend treat: free cookie with any latte" (SUN · X)
  - "Publishing to" (+ Instagram, TikTok, X, LinkedIn, YouTube, +8 more chips)
  - "How did last week's posts do?"
  - Reach 24.5K +18% · Engagement 6.1% +2.3pt · New followers 312 +9% · "Best day Saturday · 11:30"
  - "Stop posting to five apps by hand."
  - "Connect ChatGPT, Claude, or any MCP client"

## Creative Direction
- Tone preset: default
- Creative direction: agentic launch film — one prompt, a whole week of posts
- Interpretation: Playful, clean, postable. Fast motion, snappy transitions, but every readable line holds its floor. Humor from matter-of-fact competence.
- Angle: The scheduler that schedules itself. Recreate the product's own working-app demo: prompt → agent works → calendar fills → numbers report.
- Hook: A prompt typing itself into a chat card on a dark stage with keyboard ticks.
- Outro / punchline: "Stop posting to five apps by hand." + brand chip (TryPost · $19/mo · unlimited accounts & seats · trypost.it).
- Avoid: generic SaaS language, abstract filler visuals, unrelated redesign, waveform/equalizer graphics, real user data.

## Visual Identity — LOOK line
Warm-paper product UI with crisp comic-product borders: ground light #faf8f5 (scenes 3–4) and dark demo stage #0a0a0a (scenes 1–2, 5); ink #0a0a0a, white on dark #ffffff; violet primary #7c3aed, lavender chip #ede9fe, accent ink #5b21b6, yellow highlight #fde047; cards 2px solid #0a0a0a with 4-6px offset hard shadow on paper, 1px #ffffff20 border on dark; display Figtree 800 (sans), serif accent Instrument Serif 400 italic, UI labels 12-14px Figtree 600; text sizes: hero words ~150-170px, scene titles 64-88px, card copy 26-32px; violet radial glow (15-25% alpha) on dark stages only; BANNED: Inter default blue, soft rounded pastel gradients, drop shadows on text, stock "streamline" language.

## Storyboard
Use the storyboard in `~/brag-output/brag-plan.md` as the creative contract.

Scene summary:
1. The prompt — 3.5s — dark stage, chat input card, prompt types char-by-char, quiet line under card; keyboard ticks
2. The agent answers — 3.5s — reply bubble with typing dots → success chip "Scheduled 3 posts to Instagram, TikTok, and X" slams in
3. The calendar fills — 4.5s — paper world; calendar card fills with 3 rows (beat-grid ~0.95s apart) then "Publishing to" chips; hold full set
4. Last week's report — 4.5s — "How did last week's posts do?" + 3 stat cards pop (~1.1s apart) with count-ups; footer "Best day Saturday · 11:30"
5. The punchline — 3.0s — dark stage; "Stop posting to five apps by hand." word-by-word; brand chip lands; bell; fade out

## Audio
- Audio role: dense rhythmic layer under scenes 1–3, open for the stat payoff, warm fade under the outro
- Audio arc: music enters at 0 with typing; steady energy through calendar; percussive SFX thin out for stats; single bell on brand chip; music fades ~17.5s
- Music: assets/music/happy-beats-business-moves-vol-10-by-ende-dot-app.mp3 — data-start 0, data-duration 19, data-track-index 10, data-volume 0.32, data-fade-out 1.5
- Music cue guidance: bundled preset at /data/data/com.termux/files/home/.agents/skills/brag/assets/music/cues/happy-beats-business-moves-vol-10-by-ende-dot-app.music-cues.json (tempo ~110 BPM, beat ≈ 0.545s). Strong cues in the 0–19s excerpt: 15.82s (0.96), 18.01s (0.97), 18.55s (0.98). Beat grid starts 0.27, step ~0.545s. Also run `npx hyperframes beats` after wiring for the project-local grid.
- Beat locks planned: stat card 3 payoff ≈ 15.82s (±0.15s); brand chip ≈ 18.55s (±0.15s). Sequential readable reveals snap to every OTHER beat (≥0.9s apart); non-text accents may ride single beats (±0.10s).
- Audio-reactive treatment: subtle; RMS/bass modulates the violet glow halo behind the chat card (scenes 1–2) and the calendar card's soft violet shadow (scene 3). Extraction via the media-use audio-reactive workflow (audio/scripts/extract-audio-data.py from the media-use skill); if extraction is unavailable, note it and skip — do not block render.
- Audio-coupled moments:
  - Scene 1 typing — randomized keyboard/keypress-*.wav per character (0.35–0.45 volume)
  - Scene 2 chip landing — impact/impactSoft_medium_001
  - Scene 3 rows — casino/card-place-1.ogg per row landing; ui clicks on chips
  - Scene 4 cards — casino/chips-stack-1.ogg per card; soft success tick at count-up end (~15.82s)
  - Scene 5 chip — impact/impactBell_heavy_000.ogg
- SFX selection guidance: motion-matched, low-HF-risk first (impact family), casino card sounds for card-like reveals, restraint during dense text holds. SFX analysis: /data/data/com.termux/files/home/.agents/skills/brag/assets/sfx/sfx-analysis.md
- Exact SFX choice: Hyperframes chooses filenames, timestamps, density, and volume after the animation exists.
- Audio files: copy music + chosen SFX into composition/assets/ (music under assets/music/, SFX under assets/sfx/...). All paths relative, no leading slash.

## Hyperframes Instructions
Load `hyperframes` (contract + data-* timing, references/format.md; references/motion.md; references/look.md), `hyperframes-registry`, `media-use`, `hyperframes-cli`. /brag skips the hyperframes storyline step: no references/types/*, no references/story.md, no storylines, no SPEC.md — the brag plan and this brief replace them (the LOOK line is above). Skip hyperframes `usage`/`history`/`feedback`/REVIEW.md steps; `check` is brag's gate. Do not route into the generic launch-video workflow.

Requirements:
- Show at least one real UI recreation from the source (the chat card, calendar card, stat cards are all recreated from the site's demo).
- Keep all text readable: entrances 0.3–0.6s, readable lines hold ≥0.5s + 0.3s/word settled.
- Keep the video within 19s total (root data-duration 19).
- Include the planned music/SFX layer.
- Fonts: Figtree + Instrument Serif are NOT bundled — download woff2 into assets/fonts/ with @font-face in each scene file that uses them (lint fails font_family_without_font_face otherwise). Use local files only.
- Logo is recreated as type (wordmark + violet dot), no trademark image.
- Run `npx hyperframes check` before render — brag's single gate; fix every error including contrast (suggestedColor provided per finding).
- Keep creation and rendering local; remote/publishing workflows need a separate explicit user request (user HAS separately requested a filebin.net upload after render — that happens outside Hyperframes).
- The TryPost demo data on screen is the site's own fictional demo records — safe to show.
