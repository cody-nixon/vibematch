# Research Notes — Daily Problem Hunt, Feb 24, 2026

## Sources Searched

- Twitter/X via bird CLI: "someone should build", "why is there no app", "wish there was a tool", "startup idea 2026", "frustrated with AI tools", "paying too much for", "need a better way to", "nobody has built", "looking for a tool to track", "can't find a good tool for", "vibe coding broke", "ozempic tracking app", "meeting action items never get done"
- Hacker News: front page + Ask HN posts
- Reddit: r/SomebodyMakeThis, r/AppIdeas, r/Entrepreneur, r/SaaS
- Google/Brave web search: professional achievement trackers, indie game discovery apps

---

## Candidate Problems Collected (20 total)

### 1. Indie Game Discovery Broken by AI Flood
**Source:** Twitter @_summer_plays_ (reply to @edweirdsnowman thread)
> "the real problem isn't people vibe coding too much. it's that nobody has solved discovery. 100 games get built every day. 2 get played."

- **Problem:** AI/vibe-coded games are flooding platforms (Steam, Itch.io) at an unprecedented rate. Steam alone gets ~14,000 new games/year. Discovery is fundamentally broken — players have no personalized engine that matches their specific taste to buried gems.
- **Who has it:** ~50M+ Steam users, ~6M Itch.io users, casual gamers everywhere
- **Existing solutions:** SteamDB (data, not discovery), IGDB (database), SteamSpy (sales data). No Spotify-style personalization layer for games.
- **Why inadequate:** All current tools are search/filter based. None do taste-profile learning ("You loved Hollow Knight — here's what else matches your vibe").

### 2. AI Agent Unsupervised Failures (Observability Gap)
**Source:** Hacker News Ask HN "What breaks when you run AI agents unsupervised?" (11 pts, ~7 comments)
> "I spent two weeks running AI agents autonomously (trading, writing, managing projects) and documented the 5 failure modes: auto-rotation destroyed $24.88 in 2 days, documentation trap: produced 500KB of docs instead of executing, implementation gap: found bugs but never shipped fixes."

- **Problem:** Developers running autonomous AI agents have no runtime audit trail — no way to see what the agent did, why, and where it went wrong.
- **Who has it:** Every developer using Claude Code, Cursor, n8n AI workflows, OpenAI Operator
- **Existing solutions:** Langfuse (complex, LLM-level, not action-level), Helicone (API cost tracking), nothing specifically for decision audit trails
- **Note:** My past build VibeAudit scans static generated code for security. This is runtime behavior tracking — different angle, but borderline overlap in dev tooling.

### 3. Professional Achievement Tracking (Forgotten Wins)
**Source:** Hacker News (contextual signal) + search revealed market has: Forvard.org (desktop app), SuccessSnap, generic apps
- **Problem:** People forget what they accomplished at work. When performance review comes, they scramble.
- **Existing solutions:** Forvard, SuccessSnap, Notion templates
- **Assessment:** Market exists but is fragmented. AI quantification angle is differentiated. However, basic solutions already exist — not fresh enough.

### 4. Vibe Coder Session Memory (AI Context Loss)
**Source:** Twitter @chris_karani:
> "Vibe coding works until it doesn't. You can prompt your way to a working prototype, but maintaining it requires memory. The agent needs to remember why you chose that database, what tradeoffs you discussed in iteration 3."

- **Problem:** Non-technical vibe coders lose context between AI sessions — the AI doesn't know the history of the project.
- **Note:** Past build VibeAudit is in the vibe coding space. This would be a second vibe-coding tool — too close to past work.

### 5. Automated Outreach Trust Crisis
**Source:** Reddit r/Entrepreneur:
> "We automated everything and now nobody trusts anything... when I actually find friction and I talk to the person, they answer. They answer because they realize there is a human on the other side."

- **Problem:** Mass AI-generated outreach has destroyed trust in B2B communication. People don't respond because they assume it's automated.
- **Existing solutions:** Clay, Lemlist (personalization tools — but they're exactly what caused the problem)
- **Assessment:** Interesting but hard to build a compelling web product around "anti-automation."

### 6. Personal Knowledge Chaos (Too Many Notes, Can't Find Anything)
**Source:** Hacker News Ask HN "Where do you save links, notes and random useful stuff?":
> "I have 2,600+ notes in Apple Notes and can barely find anything. My kid just dumps everything into Telegram saved messages. Do you have a setup that works or is everything scattered across 5 apps like mine?"

- **Problem:** People accumulate knowledge across too many apps with no unified search or discovery layer.
- **Existing solutions:** Notion, Obsidian, Roam, Mem.ai, Readwise — extremely crowded market.
- **Assessment:** Heavily saturated. Skip.

### 7. GLP-1 Drug Journey Companion (Ozempic, Wegovy, Mounjaro)
**Source:** HN "GLP-1 Second-Order Effects" (20 pts, trending) + Twitter signals
- **Problem:** Millions on GLP-1 drugs need tracking for doses, side effects, food tolerance, progress
- **Existing solutions:** GLP-1 Diary app, MindOra (tracks Ozempic shots), Vitl (nutrition support for GLP-1 users) — market being served.
- **Assessment:** Solutions exist. Skip.

### 8. Team Burnout / Engineering Capacity Visibility
**Source:** General market signal — post-layoff era overloading teams
- **Problem:** Engineering managers can't see burnout coming until people quit. Jira shows velocity, not sustainability.
- **Existing solutions:** LinearB (engineering metrics), Jellyfish, Swarmia — relatively crowded but focused on productivity, not sustainability.
- **Assessment:** Real problem, real market, but needs org buy-in to instrument. Complex sales cycle.

### 9. Age Verification Privacy Crisis
**Source:** HN #1 story with 1,447 points, 1,107 comments: "The Age Verification Trap"
- **Problem:** Laws requiring age verification online create surveillance risks — collecting sensitive data to verify age
- **Existing solutions:** ZK proof systems being built in EU, but no consumer-facing tool
- **Assessment:** Too technical/regulatory to build as a useful web app right now.

### 10. Meeting Action Items That Fall Through
**Source:** General signal — the "meeting culture" problem
- **Existing solutions:** Otter.ai, Fireflies, Fathom (all have action item extraction). Too crowded.

### 11. Indie Developer Game Marketing / Streamer Discovery
**Source:** Same tweet thread as #1 — the other side of the discovery problem
- **Problem:** Indie developers can't find streamers or journalists to cover their game. They're drowned out.
- **Different angle than #1** — B2B side (developer → audience) vs B2C (player → game)

### 12. Local Community Decision Making
**Source:** Observational — local news dying, HOAs using email chains
- **Problem:** Neighborhoods/HOAs/small communities have no structured tool for collective decisions
- **Assessment:** Civic tech is hard to monetize. Skip.

### 13. AI Tool Fatigue + Workflow Fragmentation
**Source:** Twitter @Muruges94044849:
> "Currently using 3 different AI tools and still can't get the workflow right. Either the output is generic or it takes forever to edit."

- **Existing solutions:** LangChain, LlamaIndex orchestration, but those are for developers. Non-tech users lack a solution.
- **Assessment:** Interesting but vague as a product. Skip.

### 14. Waiting Room / Government Appointment Slot Tracker
**Source:** General knowledge — passport, DMV, immigration appointments nearly impossible to get
- **Existing solutions:** Appointment Radar (for USCIS), custom bots — but no elegant UX
- **Assessment:** Real problem but limited scope, legal gray area.

### 15. Resume Bullet Quantification
**Source:** General signal — people hate writing resumes
- **Existing solutions:** Teal, Rezi, Resume.io, and now every AI does this. Crowded.

### 16. Cold Email Research Automation
**Source:** r/Entrepreneur solofounder post about spam
- **Problem:** Quality personalized research before outreach is time-consuming
- **Existing solutions:** Clay (does this exact thing, $800+/month). Skip.

### 17. 3D Printing Hobbyist Discovery
**Source:** Brainstorm
- **Existing solutions:** Thingiverse, Printables, MakerWorld — decent and free. Not compelling enough.

### 18. Content Backlog Management (Books/Games/Videos)
**Source:** Personal observation + HN discussion
- **Problem:** People buy/save more than they consume. Massive backlogs.
- **Existing solutions:** Goodreads, Letterboxd, Backloggd — each is single-medium.
- **Note:** Cross-media "smart backlog" is interesting but niche.

### 19. Subscription Cancellation Helpdesk
**Source:** Past builds — already did CancelAssist! Skip.

### 20. SaaS Pricing Negotiation Assistant
**Source:** General market — already did SaaSWatch! Skip.

---

## Cross-Reference with PAST_BUILDS.md

Already designed/built:
- GitScout (open source issue finder)
- FlashForge (spaced repetition AI flashcards)
- PromptTele (AI teleprompter for video)
- QuoteScan (claim verification)
- SaaSWatch (SaaS price tracking)
- ToSGuard (ToS/privacy policy monitoring)
- CancelAssist (subscription cancellation)
- VibeAudit (security scanner for vibe-coded apps)
- DigestBot (GitHub codebase email digests)
- ContractorIQ (AI contractor quote comparison)
- TariffScope (tariff impact calculator)

Candidates ELIMINATED by overlap: #4 (vibe coding), #3 (partial overlap with DigestBot tracking), any more SaaS tools

---

## Top 3 Finalists

1. **Indie Game Discovery ("VibeMatch")** — personalized taste-profile matching for indie games, timed with vibe-coded game flood
2. **AI Agent Audit Log ("Replay")** — runtime behavior logging for autonomous AI agents  
3. **Indie Dev → Audience Matching** — B2B side: help indie developers find streamers/communities to cover their game

**Winner: VibeMatch** — See DECISION.md for detailed reasoning.
