# VibeMatch — Text Wireframes

All wireframes are mobile-first (375px), with desktop notes where layout differs significantly.

---

## SCREEN 1: Landing Page

```
┌─────────────────────────────┐
│  [VibeMatch logo]    [Login] │  ← Header: minimal, sticky
├─────────────────────────────┤
│                             │
│  Stop scrolling Steam       │  ← H1: bold, large (36px)
│  for 45 minutes.            │
│                             │
│  Find your next indie game  │  ← Subtitle: muted, 18px
│  in 60 seconds.             │
│                             │
│  ┌─────────────────────────┐│
│  │   🎮 Find My Match      ││  ← Primary CTA button, full-width
│  └─────────────────────────┘│     (purple/indigo gradient)
│                             │
│  No account needed.         │  ← Trust text, muted, small
│                             │
│  ─────── or ──────          │
│                             │
│  ┌─────────────────────────┐│
│  │  🔒 Sign in with Steam  ││  ← Steam OAuth button (Steam blue)
│  └─────────────────────────┘│
│                             │
├─────────────────────────────┤
│                             │
│  HOW IT WORKS               │  ← Section label (caps, muted)
│                             │
│  1. 🎯 Tell us your vibe    │
│     Answer 6 quick          │
│     questions about how     │
│     you like to feel when   │
│     you play.               │
│                             │
│  2. 🔍 We match the feeling │
│     Our engine scans        │
│     200,000+ indie games    │
│     for your exact taste.   │
│                             │
│  3. 🎮 Play something new   │
│     Discover gems you'd     │
│     never have found on     │
│     your own.               │
│                             │
├─────────────────────────────┤
│                             │
│  EXAMPLE TASTE PROFILES     │  ← Social proof section
│                             │
│  ┌─────────────────────────┐│
│  │ 🧘 "Cozy Explorer"      ││  ← Sample profile card
│  │ Solo · Story-driven ·   ││
│  │ No stress               ││
│  │                         ││
│  │ 🎮 → Spiritfarer        ││
│  │ 🎮 → A Short Hike       ││
│  │ 🎮 → Unpacking          ││
│  └─────────────────────────┘│
│                             │
│  ┌─────────────────────────┐│
│  │ ⚔️ "Precision Hunter"   ││
│  │ Solo · Challenging ·    ││
│  │ Dark atmospheric        ││
│  │                         ││
│  │ 🎮 → Ender Lilies       ││
│  │ 🎮 → DUSK               ││
│  │ 🎮 → Ultrakill          ││
│  └─────────────────────────┘│
│                             │
│  ┌─────────────────────────┐│
│  │ 🌎 "World Builder"      ││
│  │ Creative · Relaxed ·    ││
│  │ No combat               ││
│  │                         ││
│  │ 🎮 → Terra Nil          ││
│  │ 🎮 → Townscaper         ││
│  │ 🎮 → Dorfromantik       ││
│  └─────────────────────────┘│
│                             │
├─────────────────────────────┤
│                             │
│  4,102 games matched        │  ← Social proof stats
│  this week                  │
│                             │
│  ┌─────────────────────────┐│
│  │   🎮 Find My Match      ││  ← Repeat CTA at bottom
│  └─────────────────────────┘│
│                             │
├─────────────────────────────┤
│  Footer: About · How it     │
│  works · For Developers     │
│  Privacy · Terms            │
└─────────────────────────────┘
```

**Desktop difference:** 3-column grid for example profiles. Hero is two-column (copy left, animated game card stack right). Wider margins.

**Interactions:**
- "Find My Match" → navigate to Quiz (Screen 2)
- "Sign in with Steam" → Steam OAuth, then quiz, then results
- Profile cards are static (no click in v1)

---

## SCREEN 2: Vibe Quiz — Question Card

Questions are shown one at a time, full-screen card style.

```
┌─────────────────────────────┐
│  VibeMatch     [Skip quiz]  │  ← Minimal header, skip option
│                             │
│  ● ● ○ ○ ○ ○ ○ ○           │  ← Progress dots (8 questions now with negatives)
│                             │
├─────────────────────────────┤
│                             │
│                             │
│  How long are your          │  ← Question text, large (28px)
│  usual gaming sessions?     │
│                             │
│                             │
│  ┌─────────────────────────┐│
│  │ ⚡ 20-30 minutes        ││  ← Option A
│  │   Quick bursts          ││
│  └─────────────────────────┘│
│                             │
│  ┌─────────────────────────┐│
│  │ ☕ About an hour        ││  ← Option B (selected = purple border)
│  │   Sweet spot            ││
│  └─────────────────────────┘│
│                             │
│  ┌─────────────────────────┐│
│  │ 🌙 3+ hours             ││  ← Option C
│  │   I lose track of time  ││
│  └─────────────────────────┘│
│                             │
│                             │
│  ← Back            Next →   │  ← Navigation (Next activates after selection)
│                             │
└─────────────────────────────┘
```

**All 8 questions:**
1. Session length (20min / 1hr / 3hr+)
2. "Your perfect game moment felt..." (satisfied-clever / heart-moved / adrenaline / wonder-explored)
3. "The world looks like..." (pixel cozy / dark & moody / vibrant colorful / minimalist abstract)
4. "You prefer playing..." (solo / coop with friends / don't care)
5. "Story in your game is..." (everything / nice to have / in the way)
6. "What keeps you going?" (getting better at a skill / uncovering secrets / completing collection / building something)
7. "Which do you NOT enjoy?" (multi-select: Horror / Heavy grind / Wall of text / Complex management / PvP)
8. "Which of these is NOT you?" (multi-select: Trophy hunter / Speedrunner / Min-maxer / Lore-reader)

**Interactions:**
- Tap/click an option to select (immediate selection, no confirm needed)
- "Next" button becomes active after selection
- Animated slide-left transition between questions
- "Skip quiz" → jumps to seed games selection (Screen 3)
- "Back" → return to previous question

---

## SCREEN 3: Seed Games (Optional)

```
┌─────────────────────────────┐
│  VibeMatch     [Skip]       │
│                             │
│  ● ● ● ● ● ● ● ● ●        │  ← Final step dot
│                             │
├─────────────────────────────┤
│                             │
│  Name a game you love.      │  ← Heading
│  (Optional but makes        │
│  matches much better)       │  ← Subheading, muted
│                             │
│  ┌─────────────────────────┐│
│  │ 🔍 Hollow Knight...     ││  ← Search input, autofocus
│  └─────────────────────────┘│
│                             │
│  ─── RESULTS ───            │
│  ┌─────────────────────────┐│
│  │ [img] Hollow Knight     ││
│  │       Team Cherry · 2017││
│  │       Metroidvania      ││  ← Search result row (tap to add)
│  └─────────────────────────┘│
│  ┌─────────────────────────┐│
│  │ [img] Hollow Knight:    ││
│  │       Silksong (TBA)    ││
│  └─────────────────────────┘│
│                             │
│  ADDED (2/3 max)            │  ← Added games section
│  ┌─────────────────────────┐│
│  │ [img] Hollow Knight  ✕  ││  ← Added game with remove button
│  └─────────────────────────┘│
│  ┌─────────────────────────┐│
│  │ [img] Stardew Valley ✕  ││
│  └─────────────────────────┘│
│                             │
│  ┌─────────────────────────┐│
│  │   ✨ Find My Matches    ││  ← CTA (active even with 0 added)
│  └─────────────────────────┘│
│                             │
└─────────────────────────────┘
```

**Interactions:**
- Search is live (debounced 300ms), calls `/api/games/search`
- Tap result → adds to "ADDED" list (max 3 games)
- ✕ on added game → removes it
- "Find My Matches" → triggers calibration API → navigates to Results (Screen 4)
- "Skip" → same as "Find My Matches" with 0 seed games (uses invisible archetypes)

---

## SCREEN 4: Results — Game Match Stack

```
┌─────────────────────────────┐
│  VibeMatch         [Save]   │  ← "Save" = prompt account creation
│                             │
│  🎯 Your Gaming Vibe:       │
│  "Atmospheric explorer      │  ← Taste summary line, important!
│  who loves a good story     │
│  in quiet 1-hour sessions"  │
│                             │
├─────────────────────────────┤
│                             │
│  ┌─────────────────────────┐│
│  │                         ││
│  │   [Game Cover Art]      ││  ← Large cover art (60% of card height)
│  │   (tall, full-bleed)    ││
│  │                         ││
│  │─────────────────────────││
│  │ 📌 Atmospheric RPG      ││  ← Vibe tag (matches user's profile)
│  │                         ││
│  │ ENDER LILIES:           ││  ← Game title (large, bold)
│  │ QUIETUS OF THE KNIGHTS  ││
│  │                         ││
│  │ ⭐ 96%  ·  $14.99  ·    ││  ← Stats row
│  │ ~18 hours               ││
│  │                         ││
│  │ "Your love of Hollow    ││  ← Why-text (italic, quote style)
│  │ Knight's haunting       ││
│  │ atmosphere maps         ││
│  │ perfectly to Ender      ││
│  │ Lilies' ruined kingdom  ││
│  │ and deliberate pacing." ││
│  │                         ││
│  │ [View on Steam →]       ││  ← Affiliate link CTA
│  └─────────────────────────┘│
│                             │
│  ╔═══════════════════════╗  │
│  ║  ❌ Pass  💜 Love  ✅  ║  │  ← Action row (Pass / Love / Already Played)
│  ╚═══════════════════════╝  │
│                             │
│  3 of 10 matches            │  ← Progress indicator
│                             │
└─────────────────────────────┘
```

**Interactions:**
- Swipe left = Pass
- Swipe right = Love  
- Swipe up = Already Played (marks as played, no vector update)
- Tap "❌ Pass" / "💜 Love" / "✅ Played" buttons = same as swipe
- After 3 ratings: card subtly changes — "Your matches are getting sharper 🎯"
- After 10 cards: empty state (Screen 4b)
- "View on Steam →" opens Steam store in new tab (affiliate link)
- "Save" button in header → account creation prompt (Screen 6)

**Desktop difference:** Cards are ~400px wide, centered, with keyboard shortcuts shown:
- → arrow = Love
- ← arrow = Pass
- ↑ arrow = Already Played

---

## SCREEN 4B: Results Empty State

```
┌─────────────────────────────┐
│  VibeMatch         [Save]   │
│                             │
├─────────────────────────────┤
│                             │
│         🎮                  │
│                             │
│  You've seen all your       │  ← Empty state heading
│  current matches!           │
│                             │
│  New indie games drop       │  ← Explanation
│  every day. Come back       │
│  Monday for fresh picks.    │
│                             │
│  ┌─────────────────────────┐│
│  │ 📧 Email me new drops   ││  ← Secondary CTA (saves email + creates account)
│  └─────────────────────────┘│
│                             │
│  ─── OR ───                 │
│                             │
│  ┌─────────────────────────┐│
│  │ 🔍 Describe your mood   ││  ← Vibe search CTA
│  └─────────────────────────┘│
│                             │
│  YOUR LOVED GAMES (3)       │  ← Summary of what they loved
│  [Ender Lilies cover]       │
│  [Hades cover]              │
│  [Disco Elysium cover]      │
│                             │
└─────────────────────────────┘
```

---

## SCREEN 5: Vibe Search

```
┌─────────────────────────────┐
│  ← Back to matches          │
├─────────────────────────────┤
│                             │
│  Describe what you want     │  ← Heading
│  to feel.                   │
│                             │
│  ┌─────────────────────────┐│
│  │ I want something lonely ││
│  │ and beautiful with no   ││  ← Multi-line text input, placeholder
│  │ combat...               ││     with examples below
│  └─────────────────────────┘│
│                             │
│  TRY THESE:                 │  ← Example queries (tappable chips)
│  [funny and weird]          │
│  [scary but not horror]     │
│  [like Minecraft but chill] │
│  [I have 20 minutes]        │
│  [game I can quit anytime]  │
│                             │
│  ┌─────────────────────────┐│
│  │   🔍 Find matches       ││
│  └─────────────────────────┘│
│                             │
└─────────────────────────────┘

─── After search: ───

┌─────────────────────────────┐
│  ← Back                     │
│                             │
│  Matches for "lonely and    │  ← Query echo + interpretation
│  beautiful, no combat"      │
│                             │
│  We heard: "calm atmospheric│  ← LLM interpretation
│  exploration, meditative"   │
│                             │
├─────────────────────────────┤
│                             │
│  ┌─────────────────────────┐│
│  │ [cover] Journey         ││  ← Result card (compact list style)
│  │ ⭐ 97% · Free on PS · $15 Steam │
│  │ "Wordless and           ││
│  │ breathtaking"           ││
│  │ [View on Steam →]       ││
│  └─────────────────────────┘│
│                             │
│  ┌─────────────────────────┐│
│  │ [cover] ABZÛ            ││
│  │ ⭐ 92% · $19.99         ││
│  │ "Meditative underwater  ││
│  │ exploration, no enemies"││
│  └─────────────────────────┘│
│                             │
│  [Load 5 more]              │
│                             │
└─────────────────────────────┘
```

---

## SCREEN 6: Account Creation Prompt (Modal)

Appears when user clicks "Save" or "Email me new drops":

```
┌─────────────────────────────┐
│               ✕             │
│                             │
│  Save your gaming vibe.     │  ← Modal heading
│                             │
│  You've rated 7 games and   │  ← Personalized context
│  loved 3. Don't lose it.    │
│                             │
│  ┌─────────────────────────┐│
│  │ 🔒 Continue with Steam  ││  ← Primary: Steam OAuth
│  └─────────────────────────┘│
│                             │
│  ─── OR ───                 │
│                             │
│  ┌─────────────────────────┐│
│  │ 📧 your@email.com       ││  ← Email input
│  └─────────────────────────┘│
│                             │
│  ┌─────────────────────────┐│
│  │   Continue              ││  ← Sends magic link
│  └─────────────────────────┘│
│                             │
│  We'll email you a magic    │  ← No password explanation
│  sign-in link. No password. │
│                             │
│  By continuing, you agree   │  ← Legal (small, muted)
│  to our Terms & Privacy.    │
│                             │
└─────────────────────────────┘
```

---

## SCREEN 7: Public Profile Page

URL: vibematch.gg/@playername

```
┌─────────────────────────────┐
│  VibeMatch         [Login]  │
│                             │
├─────────────────────────────┤
│                             │
│  [avatar]  PlayfulSloth42   │  ← User display name
│                             │
│  ─── Gaming Vibe ───        │
│                             │
│  "Atmospheric explorer      │  ← Taste summary (the card)
│  who loves a good story,    │
│  best in quiet sessions"    │
│                             │
│  🎯 Precision ●●●●○         │  ← Vibe dimensions (radar-style text)
│  🌙 Moodiness ●●●●●         │
│  📖 Story ●●●●○             │
│  😌 Chill ●●●○○             │
│                             │
│  TOP LOVES (3)              │
│  [Hollow Knight cover]      │
│  [Disco Elysium cover]      │
│  [Elden Ring cover]         │
│                             │
│  THEIR CURRENT TOP MATCHES  │
│  ┌─────────────────────────┐│
│  │ [cover] Signalis        ││
│  │ ⭐ 97% · $14.99         ││
│  │ [View on Steam →]       ││
│  └─────────────────────────┘│
│  ┌─────────────────────────┐│
│  │ [cover] Dread Templar   ││
│  │ ⭐ 90% · $9.99          ││
│  └─────────────────────────┘│
│                             │
│  ┌─────────────────────────┐│
│  │   🎮 Find MY Matches    ││  ← CTA for viewer to start their own
│  └─────────────────────────┘│
│                             │
│  Share:                     │
│  [Copy link] [Twitter] [Discord] │
│                             │
└─────────────────────────────┘
```

---

## SCREEN 8: Dashboard (Logged-In Home)

```
┌─────────────────────────────┐
│  VibeMatch   [avatar] →     │  ← Header with avatar dropdown
│                             │
├─────────────────────────────┤
│                             │
│  Hey PlayfulSloth! 👋        │
│  Your vibe hasn't changed   │  ← Context-aware greeting
│  in 12 days. Still right?   │
│                             │
│  [Refresh my vibe] [Keep it]│  ← Recalibration prompt
│                             │
├─────────────────────────────┤
│                             │
│  YOUR MATCHES               │  ← Main section
│                             │
│  [Filter: Platform ▼]       │
│  [Filter: Price ▼]          │
│  [Filter: Length ▼]         │
│                             │
│  [Game cards in swipe stack]│  ← Same as Screen 4
│                             │
├─────────────────────────────┤
│                             │
│  NEW THIS WEEK              │  ← Below the fold
│  (3 new games match you)    │
│                             │
│  [compact game cards ×3]    │
│                             │
├─────────────────────────────┤
│                             │
│  YOUR HISTORY               │
│  Loved (18) · Passed (34)   │
│  Played (7)                 │
│                             │
│  [View loved] [View played] │
│                             │
└─────────────────────────────┘
```

---

## SCREEN 9: Settings / Account

```
┌─────────────────────────────┐
│  ← Back        Settings     │
│                             │
├─────────────────────────────┤
│                             │
│  PROFILE                    │
│  Display name               │
│  [PlayfulSloth42        ]   │
│                             │
│  Public profile URL:        │
│  vibematch.gg/@playfulsloth42│
│  [Copy link]                │
│                             │
│  ─────────────────────────  │
│                             │
│  EMAIL DIGEST               │
│  ◉ On  ○ Off                │  ← Toggle
│  Sent: every Monday morning │
│                             │
│  ─────────────────────────  │
│                             │
│  TASTE PROFILE              │
│  Last calibrated: 12 days ago│
│  [Recalibrate my taste]     │
│  [Reset all ratings]        │
│                             │
│  ─────────────────────────  │
│                             │
│  PLATFORMS (v2)             │
│  ☑ PC / Steam               │
│  ☐ Nintendo Switch          │  ← Grayed out with "Coming soon"
│  ☐ PS5                      │
│  ☐ Xbox / Game Pass         │
│                             │
│  ─────────────────────────  │
│                             │
│  CONNECTED ACCOUNTS         │
│  Steam: Connected           │
│  [Disconnect]               │
│                             │
│  ─────────────────────────  │
│                             │
│  [Sign out]                 │
│  [Delete account]           │
│                             │
└─────────────────────────────┘
```

---

## SCREEN 10: Loading States

**Quiz → Results transition:**
```
┌─────────────────────────────┐
│  VibeMatch                  │
│                             │
│                             │
│     ✨ Finding your games   │
│                             │
│  [animated progress bar]    │
│                             │
│  Scanning 200,000+ indie    │
│  games for your vibe...     │
│                             │
│  ▸ Filtering by mood        │  ← Animated checklist
│  ▸ Matching atmosphere      │
│  ✓ Found cozy explorers     │
│  ▸ Finding hidden gems...   │
│                             │
│  (Usually takes ~5 seconds) │
│                             │
└─────────────────────────────┘
```

**Vibe search loading:**
```
┌─────────────────────────────┐
│                             │
│  🔍 Understanding your vibe │
│     [spinner]               │
│                             │
└─────────────────────────────┘
```

---

## SCREEN 11: Weekly Digest Email (Text Layout)

```
Subject: 3 new indie games match your vibe 🎮

[VibeMatch logo]

Hey PlayfulSloth42,

New this week that match your "atmospheric explorer" vibe:

──────────────────────────────

🎮 SIGNALIS                   ← Game 1
   Survival horror RPG
   ⭐ 97% on Steam · $14.99
   
   Your match: You love Hollow Knight's haunted 
   atmosphere and Disco Elysium's dense lore. 
   Signalis does both in a rusted sci-fi nightmare.
   
   [View on Steam →]

──────────────────────────────

🎮 LUNACID                    ← Game 2
   First-person dungeon crawler
   ⭐ 94% on Steam · $9.99 (SALE: $6.99!)
   
   Your match: Deliberate exploration, no hand-holding,
   deeply moody aesthetic.
   
   [View on Steam →]

──────────────────────────────

🎮 SABLE                      ← Game 3
   Open-world exploration
   ⭐ 85% on Steam · Free on Game Pass
   
   Your match: Desert wandering, no combat, story
   at your pace.
   
   [View on Steam →]

──────────────────────────────

See all your matches → vibematch.gg

──────────────────────────────
You get this because you saved your gaming vibe.
[Change preferences] [Unsubscribe]
```

---

## Mobile Layout Notes

- All quiz questions: full-screen, single question visible, no scrolling needed
- Game cards: 90vw wide, centered, with visible next card peeking 10px behind
- Bottom nav bar (logged in): Home | Search | Profile | Settings
- Tap targets: minimum 48px height for all interactive elements
- Font: system-ui stack — no custom font load for performance
- Dark mode: supported via CSS prefers-color-scheme (dark theme default for gaming aesthetic)

---

## Copy / Microcopy Reference

**Navigation:**
- "Find My Match" (CTA, not "Start Quiz")
- "Find MY Matches" (profile page CTA for visitors — personal ownership word)
- "View on Steam →" (not "Buy on Steam" — some games are free)

**Empty states:**
- No more matches: "You've seen everything we have right now. More drops Monday."
- No ratings yet: "Rate a few games to sharpen your matches."
- Account not saved: "Log in to save your vibe and get Monday drops."

**Error states:**
- IGDB down: "Game search is taking a break. Try again in a few minutes."
- No search results: "We don't have that game yet. Try a similar title."
- Vibe search failed: "Couldn't read that vibe. Try describing it differently."

**Onboarding:**
- After 1st love: "Nice. Your taste fingerprint is forming. 🎯"
- After 3rd love: "Your matches are getting much sharper."
- After 5th rating: "Save your profile so you never lose these."
