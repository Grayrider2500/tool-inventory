# Chris Cross — Project Command Center & Development Context

## About Chris

- **Age:** 63, married to Patty
- **Background:** 20-year NYSP Sergeant, disability retired 2007 after herniated L-spine discs (3 discs, on-duty injury 2006)
- **Military:** 6 years USAF and National Guard
- **Location:** 35 acres, Northwest Alabama
- **Health:** Chronic back pain, a-fib, sleep apnea, HBP (all under treatment), healing right rotator cuff (MRI clear, no structural damage)

## How Chris Works Best

- **Mornings** are best for new tasks, learning, and complex thinking — mental fatigue sets in by afternoon
- **Dopamine-driven** — gets excited starting new projects, loses momentum quickly
- Prefers tools and apps with **enough complexity to hold interest** — too simple is boring
- Works best with **small, completable steps** that build toward a finish line
- **Strong reading comprehension**, notices some decline in mental acuity in recent years
- Has more interests and projects than hours in a day — this is a capacity problem, not a motivation problem

## Current Projects (as of March 2026)

### Active
- **Guest Bathroom Remodel** — ~80% complete
  - Remaining: finish tiling, glass block wall, wainscoting, curved shower door
  - Right rotator cuff injury occurred during this project
  - Should be the **first project pushed to completion**
- **Stake & Tenon Sharpeners** (Machine Shop) — ongoing production for Amish market
  - 8+ year relationship with Amish community
  - Compensated for time and materials, does not technically "work" due to disability retirement
  - Stays focused on machining due to safety and precision demands
- **Learning to Draw** — to support 3D modeling in Fusion 360 and Blender for 3D printing and machining

### Lower Priority / Background
- Various woodworking projects at different stages
- Learning Fusion 360 and Blender (3D modeling for printing and machining)
- Frustrated aspiring programmer — has tried many times, gets stuck on specific concepts

### Recurring
- **Mowing** — ~10 acres, summer seasonal commitment
- **Meal prep** — lunch and dinner daily for Chris and Patty
- **Grocery shopping** — Chris handles all of it
- **Social meals** — periodic meals with friends, requires planning

---

## App 1: Project Command Center

**File:** `project-command-center.html` — single-file HTML/CSS/JS, iPad-optimized

### Features
- **Dashboard tab**
  - Condition panel: Weather, Body (Good/Limited/Rough Day), Time (Plenty/Some/Tight), Outdoors
  - Energy level slider (0–100)
  - Help Available toggle
  - Dynamic priority scoring that weighs all conditions against each project's factors
  - TOP PRIORITY banner on highest-scoring active project
  - Quick +/−10% progress buttons on cards
  - Project detail modal with task lists (tagged Morning/Afternoon/Anytime)
  - Views: Priority, Category, Progress, On Hold
  - Stats overview: total, active, complete, avg progress

- **Schedule tab**
  - Day timeline (5am–10pm) with live "now" red line
  - Time block types: Routine/Daily, Medical/Health, Amish/Work, Social/Meals, Travel/Trip, Meal Prep, Grocery/Errands, Personal
  - Recurring blocks (Daily, Weekly, Weekdays, Custom days)
  - Mini calendar with dots on days that have blocks
  - Upcoming blocks list
  - Free time calculator

### Priority Scoring Logic
- Importance × 1.5 + Urgency × 1.5 + Progress/10
- Condition modifiers: weather dependency, help availability, physical demand vs body state, deadline flag, morning tag vs time of day, energy level

### Storage
- localStorage keys: `pcc4_proj`, `pcc4_blk`, `pcc4_cond`
- Data is device/browser specific — no cross-device sync yet

### iPad Notes
- Minimum 44–52px touch targets, pinch-to-zoom disabled
- `apple-mobile-web-app-capable` meta — add to home screen via Safari Share → Add to Home Screen

---

## App 2: Tool & Equipment Inventory

**File:** `tool-inventory.html` — single-file HTML/CSS/JS

### Purpose
Track all tools and equipment across the property so Patty has a complete record with estimated values for estate/insurance purposes.

### Fields Per Tool
- Name, Brand/Manufacturer, Category, Location
- Serial Number, Condition (Excellent/Good/Fair/Poor)
- Purchase Year (year-only supported), Purchase Price, Estimated Current Value (separate field)
- Notes (accessories, mods, details for Patty)
- Up to 2 photos (stored as base64 in localStorage)

### Categories
Machining, Woodworking, Carpentry, Power Tools, Hand Tools, Electrical, Outdoor/Land, Measuring, Other

### Locations (pre-loaded)
Main Shop, Wood Shop, House, Storage/Barn, Other

### Features
- Grid and List view toggle
- Search (name, brand, serial, notes)
- Filter by Category, Location, Condition
- Sort by name, value high/low, category, location, recently added
- Summary bar: total estimated value + breakdown by location
- **Backup (Export)** — downloads dated `.json` file: `tool-inventory-YYYY-MM-DD.json`
- **Restore (Import)** — reads a backup `.json` with two modes:
  - **Merge** — adds new records, skips duplicates matched by ID (safe, non-destructive)
  - **Replace All** — wipes current data and loads backup fresh
- Print view — clean black-and-white printable layout with "Prepared for Patty Cross" header

### Storage
- localStorage key: `cross_tools_v1`
- Photos stored as base64 inside tool records — backup files can be large with many photos

### Design
- Matches Command Center aesthetic: dark industrial theme, Share Tech Mono + Barlow Condensed fonts, amber/blue/green accent palette
- Category color bars on cards (each category has a unique color)

### Hosting
- **GitHub repo:** https://github.com/Grayrider2500/tool-inventory
- **Live URL:** https://grayrider2500.github.io/tool-inventory/tool-inventory.html
- Deployed via GitHub Pages (master branch, root path)
- To update after edits:
  ```bash
  cd "/Users/chriscross/Documents/Tool Inventory"
  git add tool-inventory.html
  git commit -m "describe what changed"
  git push
  ```
  Live URL updates automatically within ~2 minutes of push.

---

## Development Environment (Mac Mini — Chris's Shop)

| Tool | Version | Status |
|------|---------|--------|
| Git | 2.53.0 | ✅ Installed |
| Node.js | 24.14.0 | ✅ Installed |
| Claude Code | Latest | ✅ Installed |
| GitHub CLI (gh) | 2.88.0 | ✅ Installed via Homebrew, authenticated as Grayrider2500 |
| Xcode | Latest | ✅ Downloaded and ready |
| VS Code | Latest | ✅ Active — primary editing environment |

- Machine: `Chris-Shop-Mac-mini` (Mac Mini)
- User: `williamcross`
- Claude Code installed with `sudo npm install -g @anthropic-ai/claude-code`
- Chris uses **Claude Code inside VS Code** as his primary development workflow
- GitHub account exists — repo not yet created for these apps

## GitHub / Hosting

Both apps are deployed via GitHub Pages. GitHub account: **Grayrider2500**

| App | Repo | Live URL |
|-----|------|----------|
| Needle/Hook Tracker | https://github.com/Grayrider2500/needle-hook-tracker | https://grayrider2500.github.io/needle-hook-tracker/needle_tracker.html |
| Tool Inventory | https://github.com/Grayrider2500/tool-inventory | https://grayrider2500.github.io/tool-inventory/tool-inventory.html |

**Git workflow for any app update:**
```bash
cd "/path/to/app folder"
git add filename.html
git commit -m "describe what changed"
git push
```
Live URL updates automatically within ~2 minutes of push.

Git identity (already configured globally):
- Name: Chris C.
- Email: Grayrider2500@yahoo.com

---

## Future Project Ideas

### iPadOS Native App
- Rebuild the Command Center as a native SwiftUI app for iPad
- Xcode is now installed and ready on the Mac Mini
- Good first Xcode project — logic/design already figured out in the HTML version
- SwiftUI's declarative style suits Chris's mechanical/precision thinking
- Hold until a focused morning session is available

### Programming Learning
- Chris has repeatedly stalled on specific programming concepts
- Approach: use mechanical/precision thinking as analogy bridge
- SwiftUI likely more approachable than previous attempts
- Concrete goal (Command Center rebuild) will help sustain engagement

---

## Notes for Future Claude Sessions

- Always suggest **small, specific next steps** — not big vague goals
- Bathroom remodel is highest-completion-priority physical project
- Meal prep (lunch + dinner) + grocery = ~2–3 hidden hours/day — always factor into scheduling
- Morning sessions best for learning/new concepts; afternoon better for physical/routine
- **Do not oversimplify** — Chris disengages when explanations feel dumbed down
- The Amish machining work has natural accountability (real customer) — use as a model
- Chris is actively building dev skills via Claude Code in VS Code — encourage this, it's working
- When starting a new session, ask Chris to share this file for full context
- Both apps use the same dark industrial aesthetic — maintain consistency in future features
