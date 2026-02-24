# Decision: VibeMatch — Personalized Indie Game Discovery

## Selected Problem

**The Indie Game Discovery Crisis of 2026**

Steam now adds ~14,000 new games per year. Itch.io has 200,000+ titles. Vibe coding and AI game development tools have accelerated this further — in 2026, "100 games get built every day, 2 get played" (source: Twitter, @_summer_plays_ in the @edweirdsnowman thread on vibe coding). 

The discovery problem is not that good games don't exist. It's that the machinery for matching players to the right game — based on HOW they play and WHAT they feel when they play — simply doesn't exist in any meaningful form.

Current tools are database-minded:
- **Steam Discovery Queue**: Algorithmic but based on generic tags and playtime, not actual taste articulation. It recommends games you already know about.
- **SteamDB**: Data-heavy, developer-focused, not a discovery engine.
- **IGDB**: Database/API, not consumer-facing discovery.
- **SteamSpy**: Sales analytics, not personalization.
- **OpenCritic / Metacritic**: Review aggregators, not taste matchers.

Nobody does: *"You loved the oppressive atmosphere and precise platforming of Hollow Knight and the lo-fi warmth of Stardew Valley — here are 7 buried indie gems you'd love, ranked by why."*

---

## Scoring Matrix

| Criterion | Score (1–5) | Reasoning |
|-----------|-------------|-----------|
| **Urgency** | 5 | Vibe coding game flood is happening NOW. The tweet went viral Feb 2026. |
| **Impact** | 5 | 50M+ Steam users. Every gamer on earth has the "what do I play next?" problem. |
| **Novelty** | 5 | No direct competitor with taste-profile-based discovery. Spotify did it for music. Nobody did it for games. |
| **Feasibility** | 5 | Steam API (free), IGDB API (free), HowLongToBeat data (free). Text-based embeddings for game matching are well-understood tech. |
| **Monetization** | 4 | Steam affiliate program (up to 15%), premium taste profiles, email newsletter sponsorships, developer "feature me" program |
| **Bookmark Test** | 5 | Every gamer comes back when they finish a game, when they're bored, when they want something different. Weekly habit. |
| **Uniqueness from past builds** | 5 | Zero overlap with any of the 11 past builds. |
| **TOTAL** | **34/35** | |

---

## Why NOT the Others

**AI Agent Audit Log (Replay):**
- Real problem, but my past build VibeAudit is in the AI/developer tooling space. Two back-to-back developer tools.
- Langfuse exists as partial competition, complicates the "no existing solution" story.
- Developer tooling is my safe default — need to push into new territory.

**Professional Achievement Tracker:**
- Forvard.org, SuccessSnap already exist. Not fresh enough.
- AI quantification is differentiated but not enough to win on novelty alone.

**Automated Outreach Trust:**
- Anti-automation tools are hard to sell. The bad actors won't use them.
- Vague product shape.

---

## The Core Insight (What Makes This Different)

The fundamental problem is that **tag-based search is epistemically backwards for game discovery**.

You don't know the tag of the game you'll love next. You know *how you feel when you play games you love*. You know:
- "I love games where I feel clever after overcoming a challenge"
- "I want something I can play in 20-minute sessions"
- "I'm in a cozy mood, not a grinding mood"
- "I want the loneliness of Journey but with more interactivity"

VibeMatch works backwards from *feeling* to *game*, not from *genre tag* to *game*.

**The Spotify Analogy:** Before Discover Weekly existed, you had to search for music by genre. After Discover Weekly, music found you. VibeMatch is Discover Weekly for indie games — it learns your taste fingerprint and surfaces games you'd never find on your own.

**The 2026 Timing Angle:** AI-assisted game development is producing hundreds of new indie games weekly. Most are lost noise. But among them are genuine gems — and VibeMatch can surface them before they're buried. This creates a *first-mover discovery advantage*: the tool that helps players find the next hit before it's a hit.

---

## Target User

**Primary:** The "lapsed completionist" — someone who:
- Has 50-300 unplayed games in their Steam library
- Plays 2-4 hours/week, not 20
- Buys games during sales but rarely plays them
- Finishes a game and spends more time deciding what to play next than actually playing
- Follows gaming on social media but doesn't consume gaming journalism seriously

**Secondary:** The "indie curious" — someone who:
- Mainly plays AAA games
- Is vaguely aware indie games are "good" but doesn't know where to start
- Overwhelmed by the sheer volume, paralyzed by choice

---

## Decision: Build VibeMatch

VibeMatch solves a problem that is:
- **Felt by 50+ million people daily** ("what do I play next?")
- **Getting worse in 2026** (more games, harder to discover)
- **Uniquely solvable** with a taste-profile approach that doesn't exist yet
- **Completely different** from all 11 past builds
- **Monetizable** via affiliate links immediately, upgradeable to subscription
- **Bookmark-worthy** — you return after every game you finish

Build it.
