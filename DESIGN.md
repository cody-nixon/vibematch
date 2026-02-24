# VibeMatch — Final Design Document

---

## Executive Summary

**The Problem:** Steam adds 14,000+ games per year. Vibe coding and AI tools are flooding indie game platforms with hundreds of new titles weekly. Players spend more time choosing what to play than actually playing — and still miss the games they'd love most.

**The Solution:** VibeMatch learns *how gaming feels to you* — not what tags you like — and matches you with indie games using semantic embedding similarity. An 8-question vibe quiz + optional seed games creates a taste fingerprint. The engine surfaces buried gems you'd never find on Steam, with a one-sentence "why you'd love this" explanation for each match.

**The Difference:** Every existing tool (Steam Discovery Queue, IGDB, SteamSpy) is database-first. VibeMatch is feeling-first. You don't need to know the name of the game you'll love — you just need to know how it feels.

---

## Target User Persona

**Name:** Alex, 29  
**Occupation:** Software engineer  
**Gaming context:** Plays 5-8 hours/week. Has 180 games in Steam library, played maybe 30% of them. Buys 2-3 games per sale and rarely touches most. Finishes a game and spends 45+ minutes scrolling Steam, YouTube reviews, Reddit recommendations before picking the next one.

**Frustrations:**
- Steam's "More Like This" recommends games he already knows
- Reddit threads give contradictory recommendations
- Spending money on games that aren't right for his current mood
- Finding himself playing the same 3 games in rotation because discovery is exhausting

**Goals:**
- Find indie gems that match his specific taste, not just his demographic
- Spend less time choosing, more time playing
- Discover games before they're big (not just popular titles)

**Trigger:** Just finished Hollow Knight. Wants to capture that exact feeling again — not just "more Metroidvanias."

---

## Technical Specification

### Stack
- **Frontend:** Next.js 14 (App Router) + TailwindCSS + shadcn/ui
- **Backend:** Next.js API routes (Node.js)
- **Database:** PostgreSQL via Supabase with pgvector extension
- **Embeddings:** OpenAI text-embedding-3-small (1536 dimensions)
- **Game data:** IGDB API (free, 500 req/s) + Steam Web API (price/rating sync)
- **Auth:** Supabase Auth — magic link email + Steam OAuth
- **Email:** Resend (weekly digest)
- **Deployment:** Vercel
- **Background jobs:** Vercel Cron (daily game sync) + Trigger.dev (weekly digest)
- **Rate limiting:** Upstash Redis

### Core Database Tables
| Table | Purpose |
|-------|---------|
| `users` | Account + taste embedding vector |
| `games` | 200K+ games with description embedding vector |
| `user_ratings` | love/pass/played/wishlisted per game |
| `recommendation_history` | Shown recommendations, click tracking |
| `digest_sends` | Email digest history |

### Taste Engine Algorithm
1. **Quiz embedding:** Map 8 quiz answers to a semantic query string, embed via OpenAI
2. **Seed embedding:** Average embeddings of 1-3 user-selected loved games
3. **Initial fingerprint:** 20% quiz vector + 80% seed game average (or 100% quiz if no seeds; invisible archetypes warm the vector)
4. **After ratings:** Recompute as weighted mean of all "loved" game embeddings (quiz vector stays at 20% permanent weight)
5. **Similarity search:** pgvector cosine similarity against all non-played games
6. **Why-text:** Cluster users into 50 taste clusters; pre-generate explanations per cluster per game via GPT-4o-mini; cache aggressively

### API Surface
| Endpoint | Method | Purpose |
|---------|--------|---------|
| `/api/taste/calibrate` | POST | Initial quiz + seed games → taste vector |
| `/api/taste/rate` | PATCH | Rate a game (love/pass/played) → update vector |
| `/api/recommendations` | GET | Paginated recommendation feed |
| `/api/games/search` | GET | Autocomplete game search |
| `/api/games/vibe-search` | POST | Natural language → matching games |
| `/api/profile/:username/public` | GET | Public taste profile page |
| `/api/profile/compare` | GET | Two user profiles → shared matches |

---

## Wireframes

See WIREFRAMES.md for complete text-based wireframes covering:
- Screen 1: Landing Page
- Screen 2: Vibe Quiz (8-question card flow)
- Screen 3: Seed Games Selection
- Screen 4: Game Match Stack (swipe-style results)
- Screen 4B: Empty State
- Screen 5: Vibe Search (natural language)
- Screen 6: Account Creation Modal
- Screen 7: Public Profile Page
- Screen 8: Logged-in Dashboard
- Screen 9: Settings / Account
- Screen 10: Loading States
- Screen 11: Weekly Digest Email

---

## Implementation Roadmap

### Week 1: Data Foundation
**Goal:** 50,000 games ingested and embedded in the database.

Tasks:
- Set up Supabase project with pgvector
- Write IGDB sync script: fetch games, normalize metadata, generate embeddings
- Start with: games rated >50 reviews, released 2015-2026 (most relevant indie games)
- Store embeddings, cover art URLs, Steam links
- Set up Steam price/rating sync

**Deliverable:** 50K games in database with embeddings.

### Week 2: Taste Engine
**Goal:** Quiz → taste vector → ranked game list (no UI yet, just API).

Tasks:
- Quiz answer → semantic string → embedding function
- Seed game selection and averaging
- pgvector similarity search with filters (price, platform, length)
- Rating update logic (recalculate taste vector from all loved games)
- Unit tests for the taste engine

**Deliverable:** `POST /api/taste/calibrate` and `PATCH /api/taste/rate` working.

### Week 3: Core UI
**Goal:** Full user flow working end-to-end in browser.

Tasks:
- Landing page (static, no interaction)
- Quiz flow (8 screens, animated)
- Seed game search (debounced, IGDB autocomplete)
- Game match stack (swipe cards with cover art)
- "View on Steam" affiliate links
- Loading states

**Deliverable:** New user can complete full flow (quiz → recommendations → rate).

### Week 4: Auth + Persistence
**Goal:** Users can save and return to their taste profile.

Tasks:
- Supabase Auth: magic link + Steam OAuth
- Guest → registered user transition (merge anonymous taste data)
- Dashboard (rated games, new matches this week)
- Settings page (digest toggle, recalibrate)

**Deliverable:** Returning users see their saved taste profile and history.

### Week 5: Why-Text + Vibe Search
**Goal:** The differentiators that make VibeMatch feel intelligent.

Tasks:
- Taste cluster generation (k-means, 50 clusters)
- Why-text pre-generation per cluster × game (GPT-4o-mini, cached)
- Vibe search endpoint (user text → LLM interpretation → embedding → search)
- Rate limiting on LLM endpoints (Upstash Redis)
- Prompt injection protection on vibe search

**Deliverable:** Every recommendation card has a why-text. Vibe search works.

### Week 6: Email Digest + Public Profiles
**Goal:** Retention loop and viral sharing.

Tasks:
- Weekly digest cron job (Trigger.dev): find new matches, send via Resend
- Email template (clean, game cover images, why-text, affiliate links)
- Public profile page (`/@ username`)
- Profile sharing cards (Open Graph image generation for Twitter/Discord)
- Compare two profiles endpoint

**Deliverable:** Users get Monday emails. Profiles are shareable.

### Week 7: Polish + Launch Prep
**Goal:** Production-ready quality.

Tasks:
- Dark mode (default for gaming aesthetic)
- Mobile touch gestures on swipe cards
- SEO: individual game pages (`/game/hollow-knight`) for search indexable
- Open Graph meta for social sharing
- Error monitoring (Sentry)
- Analytics (Plausible, privacy-respecting)
- Launch on HN "Show HN", r/indiegaming, r/SteamDeals, indie gaming Discord servers

---

## Estimated Build Effort

| Component | Hours | Notes |
|-----------|-------|-------|
| IGDB game ingestion + embedding pipeline | 16h | One-time setup, then automated |
| Taste engine algorithm + API | 24h | Core intelligence, needs testing |
| Quiz + seed game UI | 12h | Interactive but not complex |
| Game card swipe UI | 16h | Swipe gestures, animation polish |
| Auth + persistence | 16h | Supabase makes this simpler |
| Why-text generation + caching | 16h | Cluster-based caching is key |
| Vibe search | 12h | LLM call + embedding search |
| Email digest pipeline | 12h | Cron + Resend |
| Public profiles + sharing | 8h | Simpler than it sounds |
| Settings + dashboard | 8h | Mostly CRUD |
| Polish (dark mode, mobile, OG images) | 16h | Important for launch |
| **Total** | **~156 hours** | **~4-5 weeks for 1 experienced full-stack dev** |

---

## Risks and Mitigations

| Risk | Likelihood | Severity | Mitigation |
|------|-----------|----------|------------|
| IGDB API breaking changes | Low | High | Cache all game data locally; IGDB changes slowly |
| OpenAI embedding model deprecation | Medium | High | Store model version per embedding; schedule re-embed job |
| Steam affiliate program policy changes | Medium | Medium | Diversify: also add GOG affiliate and Humble Bundle |
| Poor cold-start recommendations | High | High | Invisible archetype seeds; A/B test quiz quality |
| LLM costs spiraling | Medium | Medium | Cluster-based why-text caching; rate limiting |
| Player churn after finding one game | High | Medium | Weekly digest; "just finished?" re-engagement email |
| Copycat (Spotify, Steam itself copies idea) | Medium | High | Build community and data moat fast; developer portal differentiates |
| Why-text quality too generic | High | High | Example-test 50 game+profile combos before launch; human review of generated texts |

---

## Success Metrics

### Week 1 Post-Launch
- [ ] 500 quiz completions
- [ ] 200 user accounts created
- [ ] Average 8+ ratings per session
- [ ] 15%+ Steam click-through rate on recommendations

### Month 1
- [ ] 5,000 quiz completions
- [ ] 1,000 registered users
- [ ] 40%+ weekly digest open rate (email)
- [ ] 5%+ weekly return visit rate
- [ ] First affiliate commissions from Steam

### Month 3
- [ ] 25,000 quiz completions
- [ ] 5,000 registered users
- [ ] $500+ MRR from Pro tier
- [ ] 30%+ of registered users active weekly
- [ ] 50+ "I found a hidden gem through VibeMatch" tweets/posts

### The Real Success Signal
"Would someone recommend VibeMatch to a friend after it found them a game they loved?" That's the only metric that matters at first. If yes, everything else follows.

---

## What Makes This Design Different From Existing Solutions

1. **Feeling > Tags**: Every competitor asks what tags/genres you like. VibeMatch asks how you want to *feel*. This is the same insight Spotify had over Pandora — taste is emotional, not categorical.

2. **Why-text is the product**: The one-sentence "why you'd love this" explanation transforms a recommendation from a list item into a discovery narrative. Users feel understood, not categorized.

3. **2026 timing**: The vibe coding + AI game development explosion is creating a game flood problem that didn't exist at this scale 2 years ago. VibeMatch addresses a problem that is getting *worse right now*, not a perennial problem.

4. **Negative vibe matching**: Explicitly capturing "what I don't want" (horror / heavy grind / complex management) is as important as positive preferences. No competitor does this as a first-class feature.

5. **Guest-mode first**: No signup required to get value. The quiz is the product, not just a feature. This lowers friction to near-zero for the viral "share my vibe profile" use case.
