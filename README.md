# Tool & Equipment Inventory

A single-file HTML/CSS/JS app for tracking tools and equipment across a property. Designed for estate and insurance documentation purposes — gives a complete record of tools with photos and estimated values.

**Live URL:** https://grayrider2500.github.io/tool-inventory/tool-inventory.html

---

## Features

- **Add, edit, and delete tools** with a full detail form
- **Up to 2 photos per tool** stored as base64
- **Grid and List view** toggle
- **Search** by name, brand, serial number, or notes
- **Filter** by Category, Location, or Condition
- **Sort** by name, estimated value (high/low), category, location, or recently added
- **Summary bar** showing total estimated value with breakdown by location
- **⬆ Backup** — downloads a dated `.json` file: `tool-inventory-YYYY-MM-DD.json` (arrow points up = sending data out)
- **⬇ Restore** — reads a backup `.json` back in (arrow points down = bringing data in), two modes:
  - **⬇ Merge** — adds new records, skips duplicates by ID (safe, non-destructive)
  - **Replace All** — wipes current data and loads the backup fresh
- **Print view** — clean black-and-white printable layout; clicking Print opens a prompt to enter the "Prepared for" name (defaults to "Patty Cross")

---

## Fields Per Tool

| Field | Notes |
|-------|-------|
| Name | Required |
| Brand / Manufacturer | |
| Category | See list below |
| Location | See list below |
| Serial Number | |
| Condition | Excellent / Good / Fair / Poor |
| Purchase Year | Year only |
| Purchase Price | |
| Estimated Current Value | Separate from purchase price |
| Notes | Accessories, mods, details |
| Photos | Up to 2, stored as base64 |

### Categories
Machining, Woodworking, Carpentry, Power Tools, Hand Tools, Electrical, Outdoor/Land, Measuring, Other

### Locations
Main Shop, Wood Shop, House, Storage/Barn, Other

---

## Storage

- Data is stored in `localStorage` under the key `cross_tools_v1`
- Storage is browser/device specific — no cross-device sync
- Photos stored as base64 inside tool records — backup files can be large with many photos
- **Export regularly** to keep a backup outside the browser

---

## Design

- Dark industrial theme
- Fonts: Share Tech Mono + Barlow Condensed
- Accent palette: amber / blue / green
- Each category has a unique color bar on its card
- Mobile-optimized with 44–52px touch targets, pinch-to-zoom disabled
- Can be added to the iOS home screen via Safari Share → Add to Home Screen

---

## Deployment

Hosted via GitHub Pages from the `master` branch.

To update after editing `tool-inventory.html`:

```bash
cd /Users/chriscross/Git/tool-inventory
git add tool-inventory.html
git commit -m "describe what changed"
git push
```

Live URL updates automatically within ~2 minutes of push.

---

## Repository

- **GitHub:** https://github.com/Grayrider2500/tool-inventory
- **Owner:** Grayrider2500
