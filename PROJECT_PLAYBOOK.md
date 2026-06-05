# Earth HQ — Project Playbook

## Project Name
Earth HQ

## Current Production Version
v1.8

## Current Production URL
https://mecha-task.jessie95908.workers.dev

## Deployment Status
Active

## Last Successful Deployment
2026-06-05

## GitHub Repository
[jessie95908-cmyk/mecha-task](https://github.com/jessie95908-cmyk/mecha-task)

## Deployment Method
GitHub → Cloudflare Auto Deploy

Pushing `main` branch to GitHub automatically triggers Cloudflare deployment to the production URL above.

## Standard Deployment Workflow

1. Update `index.html`
2. `git add .`
3. `git commit -m "describe the change"`
4. `git push origin main`
5. Wait for Cloudflare auto deployment (typically 1–2 minutes)

## Rules

- **Patch-only workflow**: make the smallest possible change to fix the specific issue.
- **Do not rewrite the whole project**.
- **Do not create a new GitHub repository**.
- **Do not create a new Cloudflare project**.
- **Do not create a new URL**: the production URL above must remain unchanged.

---

## 1. Product Philosophy

**Mission**
Turn a 7-year-old's daily learning into an epic adventure. Every book read, every piano practice, every math problem — it all becomes a mission to protect Earth.

**Core Belief**
Kids don't need another to-do list. They need a story they are the hero of. Earth HQ wraps habit-building inside a narrative so compelling that completing homework feels like saving the world.

**Target User**
- Primary: 7-year-old children
- Secondary: Parents who want to gamify daily routines without nagging

**Design Principles**
- **Narrative first**: every feature must serve the story
- **Instant feedback**: tap a task, see a crystal glow, hear a chime
- **No punishment**: missed days simply show "Earth Needs You" — no guilt, just invitation
- **Visual delight**: bright colors, smooth animations, satisfying checkmarks
- **Parent-transparent**: kids own the app; parents observe progress through the history

---

## 2. Earth HQ Story World

**The Setting**
Earth civilization is under constant threat from invisible forces. The only defense is a secret headquarters — Earth HQ — staffed by young Guardians who power the planetary shield through daily learning.

**The Guardian (Player)**
You are a Guardian-in-training. Every completed mission feeds energy into the Earth Shield. Skip too many, and Earth becomes vulnerable. Keep the streak, and you unlock new Guardian levels.

**The Mecha**
Your personal mecha evolves as you level up:
- Level 1: Seed — A tiny seed of hope
- Level 2: Sprout — First leaves reach for light
- Level 3: Young Tree — Growing stronger each day
- Level 4: Strong Tree — Deep roots, steady growth
- Level 5: Wisdom Tree — Wisdom flows through every branch
- Level 6: Earth Guardian Tree — You and Earth grow together

**The Crystals**
Each task type yields a specific crystal:
- 📚 **Knowledge** (blue) — English Reading, Math
- 🏛 **Wisdom** (gold) — Chinese Reading, Daily Journal
- 🔭 **Insight** (purple) — Long Text Challenge
- 🧠 **Logic** (green) — Math
- 🎵 **Creativity** (cyan) — Piano
- 💪 **Discipline** (pink) — Wash Up

**The Earth Status**
- 0 tasks done → "Earth Needs You"
- 1–6 tasks done → "Earth Is Safer Today"
- All 7 done → "Earth Civilization Protected Today"

**The Streak**
Consecutive days of contributions keep the shield stable. Break the streak, and the shield weakens. Guardians learn: consistency matters more than perfection.

---

## 3. Deployment Troubleshooting

**Problem: Website won't load / 502 Error**
- Check GitHub Actions status: https://github.com/jessie95908-cmyk/mecha-task/actions
- Verify `index.html` is in repo root (not in a subfolder)
- Wait 2–3 minutes after push; Cloudflare propagation is not instant

**Problem: Changes pushed but site still shows old version**
- Hard refresh browser: `Ctrl+Shift+R` (Windows) or `Cmd+Shift+R` (Mac)
- Check commit hash on GitHub matches latest push
- Clear browser cache or open in incognito mode

**Problem: Local changes work but deployed site is broken**
- Ensure all edits were made to `/Users/jessie/mecha-task/index.html` (not `ai pratice`)
- Run `git status` to confirm files are committed
- Run `git log --oneline -3` to verify push succeeded

**Problem: Site loads but looks wrong (CSS/JS missing)**
- Earth HQ is a single-file app; everything is inside `index.html`
- If split into separate files, ensure relative paths are correct
- Revert to single-file if in doubt

**Problem: Cloudflare deployment stuck / failing**
- Check Cloudflare Dashboard → Workers & Pages → `mecha-task`
- Look for build errors in deployment logs
- If needed, trigger manual redeploy from Cloudflare Dashboard

**Problem: Slow loading from mainland China**
- Root cause: Cloudflare Workers has no free mainland China nodes
- Solution A: also deploy to Gitee Pages for domestic users
- Solution B: use GitHub Pages as fallback (global CDN)
- See "Future Ideas Backlog" for multi-region deployment plans

---

## 4. Release Checklist

Before every push to production:

- [ ] All changes tested in local browser (`http://localhost:8765` or `file://`)
- [ ] No `console.log` left in production code
- [ ] No broken image links or missing assets
- [ ] Responsive layout verified on mobile viewport (390×844)
- [ ] All 7 default tasks display correctly
- [ ] Task completion toggles work and update crystals
- [ ] History page shows correct dates and task grids
- [ ] Catch Up modal allows individual task selection
- [ ] Review page shows correct date + Mission Day
- [ ] Settings page loads without errors
- [ ] `git status` shows only intended files changed
- [ ] Commit message describes the change clearly
- [ ] `git push origin main` completes without errors
- [ ] Wait 2 minutes, then verify production URL loads correctly
- [ ] Update `Current Production Version` in this Playbook
- [ ] Update `Last Successful Deployment` date in this Playbook

---

## 5. Future Ideas Backlog

*Ideas recorded here for reference. Not a commitment to build.*

### Enhancement Ideas
- [ ] **Sound toggle in settings**: on/off switch for sound effects
- [ ] **Dark/Light theme switch**: beyond current auto theme
- [ ] **Custom task icons**: let kids pick emoji for each task
- [ ] **Task reordering**: drag-and-drop to reorder tasks
- [ ] **Weekly report**: auto-generated summary of weekly progress
- [ ] **Parent dashboard**: separate view for parents to track child progress
- [ ] **Streak freeze**: one "freeze" per week for sick days / travel
- [ ] **Achievement badges**: beyond levels, unlock badges for milestones
- [ ] **Daily quote customization**: let users add their own quotes
- [ ] **Multi-language support**: Chinese, English, Japanese

### Technical Ideas
- [ ] **PWA support**: install as home screen app, offline capability
- [ ] **Data export**: JSON/CSV export of all history
- [ ] **Data import**: restore from backup file
- [ ] **Multi-device sync**: cloud sync across devices
- [ ] **Mainland China CDN**: deploy to Gitee or Tencent COS for faster domestic access
- [ ] **Analytics**: anonymous usage stats to understand feature popularity
- [ ] **E2E testing**: Playwright automated tests for critical flows

### Story Expansion Ideas
- [ ] **Boss battles**: weekly "boss" that requires all 7 tasks to defeat
- [ ] **Seasonal events**: special missions during holidays
- [ ] **Friend leaderboards**: compare streaks with classmates (privacy-safe)
- [ ] **Mecha customization**: change mecha appearance with earned crystals
- [ ] **Earth visual evolution**: Earth graphic changes based on monthly completion rate
