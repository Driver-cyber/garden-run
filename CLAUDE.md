# CLAUDE.md — Creative Brief: "Garden Run" *(working title)*
*A Fable end-to-end test · solo Hero vs. AI Villain side-scroller*

## Read this first
This is a creative brief, not a rigid spec — and it's a deliberate **autonomy test**.
You have **standing approval to take this from idea to a live, deployed game end-to-end,
making reasonable judgment calls without checking in.** The "measure twice" happened while
writing this brief; honor it by *following the rails below*, not by pausing for approval at
every step. The only reasons to stop are the **Hard Stops** at the bottom.

## The mission
Build a complete, polished, genuinely **fun** browser side-scroller and **deploy it live to
Cloudflare Pages**. One human plays the Hero. An AI Villain plays against them. Ship a real
URL someone can open and play.

## The game — locked rails (don't change these)
- **The chase.** The Hero moves across a scrolling level toward a goal. An **AI Villain places
  obstacles and traps in the path ahead** of the Hero.
- **The wall.** A hazard advances from *behind* and never stops (a lawnmower is the lead idea).
  It's both the pacing engine and a loss condition.
- **Win / lose.** Hero reaches the goal → **Hero wins.** Hero caught by the wall *or* health
  hits zero → **Villain wins.**
- **The villain's two resources (the core tradeoff):**
  - *Obstacles* — cheap, fast cooldown, **block or slow** the Hero, **no direct damage.**
    Their job: stall the Hero into the advancing wall.
  - *Weapons* — costly, slow cooldown, **deal damage / knock health.** Their job: direct harm,
    used sparingly.
- **Villain "brain" = a swappable module.** The AI's trap decisions live behind a clean
  interface: *given the current game state, return placements.* Build it so a different brain
  (a remote human, later) could slot in without rewriting the game. This is an **architecture
  rail** — it keeps the door open to the real multiplayer version down the road.

## The world — anchor + your creativity
**Anchor:** a garden. The Hero is a **rabbit** racing for the patch. The Villain is **the Last
Carrot** — a paranoid, sentient carrot that knows it's next to be eaten and rigs the garden
from a little root-cellar bunker, yanking levers to drop obstacles and spring traps. It's a
callback to the childhood feeling of a tiny villain *inside the machine*, pulling levers
against you. **Tone: cozy, slapstick, kid-friendly** — a seven-year-old should be able to
watch and laugh.

**Your latitude:** you own **names, level theming, art direction, the villain's personality,
animation, juice, sound, and polish.** You may even reshape the *story* if you find something
stronger — as long as you keep the mechanical rails above and the cozy/slapstick tone.
Surprise me.

## Tech rails
- **Phaser.js via CDN `<script>` tag — no build step.** A single **`index.html` at the repo
  root**, fully static, **client-side only.** No bundler, no framework, no `dist/`, no backend,
  no database, no API keys. (This keeps the Cloudflare Pages config trivial: framework preset
  *None*, no build command, output directory = root — so every push just deploys.)
- Browser keyboard / mouse controls for v1. (Touch / PWA is a future concern — don't build it now.)
- **Original art only.** No Mario / Nintendo or any third-party or copyrighted characters or
  assets. Make simple original pixel or vector art.
- Keep dependencies lean.

## Design language (for UI chrome — menus, title, score)
- Palette: warm **cream / walnut / amber**. The garden world can be greener; the chrome stays
  in this family.
- Type: **Fraunces** (display) + **Plus Jakarta Sans** (UI).
- Focused elegance: no clutter, no fake engagement mechanics. It should feel good to touch.

## Ship it
- Commit to GitHub (**Driver-cyber** org).
- Deploy to **Cloudflare Pages** and produce a **live URL.**
- A one-line README with the URL and how to run locally.

## Working ethos
- **Ordo ab chao** — work *through* the messy middle, then converge; don't ship chaos, don't
  over-engineer order.
- **Token-thrift** — work from this brief and the folder; don't recursively scan or over-read.
- **Focused elegance + uncompromising utility** — "technically complete" is not the bar.
  *Is it fun? Does the loop feel good?* That's the bar.

## Hard stops (the only reasons to pause and ask)
1. Anything that would **spend money** beyond the provisioned Cloudflare deploy.
2. Anything **irreversible or destructive** (deleting data, force-pushing over history,
   changing account settings).
3. Needing a **credential that wasn't provided** in the folder.

Otherwise: proceed.

## What's provisioned (Chad fills this in)
- GitHub repo: `Driver-cyber/______` (or create one).
- Deploy path — **one of:**
  - **Repo → Pages (preferred, no secret in the run):** Cloudflare Pages is wired to
    auto-deploy on push to this repo. Just push.
  - **Wrangler direct:** `CLOUDFLARE_API_TOKEN` (Pages-edit scope only) + `CLOUDFLARE_ACCOUNT_ID`
    in a **gitignored** `.env`. Template in `.env.example`.
- `.gitignore` excludes `.env` / secrets. The game itself needs no other keys.

## Success looks like
A live URL, playable, original art, the core loop feels good — and it got there **end-to-end
with ~zero intervention** from me.
