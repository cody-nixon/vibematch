# Daily Problem Hunter Report — Feb 24, 2026

## The Problem

**Indie game discovery is broken — and vibe coding is making it worse.**

Source: Twitter thread (@_summer_plays_ replying to @edweirdsnowman, Feb 24, 2026):
> "the real problem isn't people vibe coding too much. it's that nobody has solved discovery. 100 games get built every day. 2 get played."

Secondary signal: HN "Ask HN: What breaks when you run AI agents unsupervised?" (confirming that AI automation is flooding markets — gaming is just the clearest consumer-facing manifestation).

The problem in numbers:
- Steam: 14,000+ games released per year (2026 trend accelerating with AI tools)
- Itch.io: 200,000+ games total, hundreds added weekly
- Average gamer: spends 45+ minutes deciding what to play next
- Steam Discovery Queue: tag-based, surfaces games users already know
- Result: Most indie games are invisible. Developers pour months into games that are never discovered.

## Why I Chose This

I evaluated 20 candidate problems across Twitter/X, Reddit, and Hacker News. VibeMatch scored highest on:

1. **Genuine novelty**: No one does taste-profile-based game discovery. Every existing tool (SteamDB, IGDB, Metacritic) is a database, not a matching engine.

2. **Perfect 2026 timing**: AI game development tools are flooding the market NOW. This is a problem that just got 10x worse and will keep getting worse.

3. **Zero overlap with past builds**: Completely different from GitScout (open source), VibeAudit (security), DigestBot (code digests), etc.

4. **Strong bookmark test**: Gamers return every time they finish a game. This isn't a one-time tool — it's a habit.

5. **Clear monetization path**: Steam affiliate links (15% commission) → Pro tier ($5/mo) → Developer portal (B2B $99/mo).

## Design Summary

**VibeMatch** is a personalized indie game discovery engine that works like Spotify's Discover Weekly for games.

**Core innovation:** It asks how you want to *feel* when you play, not what genre tags you want. 8-question vibe quiz + optional seed games → taste fingerprint (pgvector embedding) → semantic similarity matching across 200K+ games → results with "why you'd love this" explanations.

**Key design decisions:**
- Guest-first (no signup required) — lower friction, better viral sharing
- Negative vibe questions (what you DON'T want) — as important as positives
- Cluster-based why-text generation — makes explanations feel personal without per-user LLM calls
- Swipe card UI — feels like Tinder, not a survey
- Weekly email digest — retention loop without notification fatigue

**Build estimate:** ~156 hours (~4-5 weeks, 1 experienced full-stack dev)

## GitHub Repo

**URL:** https://github.com/cody-nixon/vibematch

**Contents:**
- `README.md` — Project overview
- `RESEARCH.md` — All 20 candidate problems with sources and analysis
- `DECISION.md` — Scoring matrix and deep reasoning for final choice
- `PLAN.md` — Technical architecture, API design, data model, stack
- `REVIEW.md` — Multi-role review (product/QA/engineering/design/security)
- `WIREFRAMES.md` — Text wireframes for 11 screens + email template
- `DESIGN.md` — Complete design document (persona, tech spec, roadmap, metrics, risks)
- `REPORT.md` — This file

## Key Insight

**The same insight that made Spotify great applies to gaming:**

Music recommendation was broken until Spotify realized: people don't know the *genre name* of the music they'll love next. They know the *feeling* they want. Discover Weekly succeeded because it translated listening behavior into emotional taste patterns.

Steam Discovery Queue treats games like Amazon treats products — by category and purchase co-occurrence. But games are emotional experiences, not products. The right question isn't "what did you buy that was similar?" but "what did you *feel* when you played the games you loved?"

**VibeMatch treats the quiz as the product** — not a filter, not a form. The 8-question vibe quiz is the core experience. Users feel understood before they see a single recommendation. That's the emotional hook that converts them into returning users.

**The vibe coding connection is the timing insight:** As AI floods the market with new games, players need a discovery layer that gets *smarter* as the volume increases. A taste-profile engine actually gets better as it has more games to match against. The flood becomes the product's best friend.
