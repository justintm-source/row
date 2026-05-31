# Lifestyle Dashboard — Session Handoff

**Live:** https://row-bice.vercel.app
**Repo:** https://github.com/justintm-source/row
**Local:** `/Users/justintorres-marck/Lifestyle Dashboard/Lifestyle Dashboard v2/row/`

---

## What got done this session (4 commits on `main`)

| Commit | What |
|---|---|
| `7dda70f` | Stopgap: copied existing single-page `dashboard.html` in as `index.html` so Vercel stopped 404-ing |
| `211b3db` | Pulled the real multi-page dashboard source from `RowanThistlebrooke/YTdashh1` — `index/health/gym/finance/po-water.html` + `topbar.js` (~400KB total). This is the base the tutorial prompts modify. |
| `2d3003c` | Applied **Phone fix** (iOS safe-area padding on gym/finance/po-water shells) + **Last UI fix** (Goals ticker single-row crossfade) |
| `fb3a88b` | Renamed to **Justin's Dashboard** and set day-tracker window to **5am–9pm** |

## Originally diagnosed problem

The Vercel 404 happened because the fork only contained prompt instruction files, never the actual dashboard code. Upstream `RowanThistlebrooke/SQL-supabase` had the same issue. The real source lived in a sibling Rowan repo, `RowanThistlebrooke/YTdashh1` — pulled from there.

## What the dashboard does (live now, localStorage-only)

- **Main** — Goals ticker, Day Ring (5am–9pm), To-Do list, Day Streak
- **Health** — Supplement stack tracker, embedded Water tracker
- **Water** — Daily target calculated from weight / age / sex / caffeine / stimulants
- **Fitness** — Workout tracker with progressive overload, multi-gym, past workouts, progress photos, weight tracking
- **Finance** (top-right 📊 icon) — Net worth + pie chart, Subscriptions, Orders, Wishlist (% of net worth)
- **Cross-page** — Water +1 button in top bar, Main/Health/Fitness bottom tabs, iOS safe-area aware, installable as a PWA

## What's left — needs your action

### Supabase setup (≈15 min)

1. Go to **supabase.com** → New Project (free tier)
2. SQL Editor → paste contents of `SQL` → Run
3. Storage → New bucket `progress-photos` → set to **Public**
4. SQL Editor → paste contents of `Gym fix 2` → Run
5. Settings → API → copy **Project URL** and **anon / publishable key**
6. Paste both into the next chat — I'll apply `VS code prompt`, `SQL 3rd`, and `GYM fix 1` in one push

### Then in order

- **Whoop integration** — Recovery / Sleep / Strain / HRV via GitHub Actions cron (architecture already designed)
- **Plaid integration** — Auto net worth via Plaid Link + GitHub Actions cron (Monarch ruled out — no public API)

## Saved to Claude memory for next session

Located at `~/.claude/projects/-Users-justintorres-marck-Lifestyle-Dashboard-Lifestyle-Dashboard-v2-row/memory/`:

- `dashboard-supabase-pending.md` — Supabase blocker + the 3 prompts waiting on credentials
- `whoop-integration-pending.md` — Recovery / Sleep / Strain / HRV approach
- `plaid-integration-pending.md` — Plaid path (Monarch ruled out)
- `user-schedule.md` — 5am–9pm awake window

When the next chat starts from this folder, Claude loads these automatically. Just say "let's keep going on the dashboard" and we're back where we left off.

## Housekeeping noted, not touched

- Nested `row/row/` folder is an accidental second `git clone` (untracked, has its own `.git`). Harmless. From inside this folder you can `rm -rf row` anytime to clean it up.
