# SATURNO MOVEMENT STUDIO - MVP HUB

**The Ableton of Movement**
Design Your Workout. Design Your Life.

## Quick Start

```bash
cd saturno-hub-starter
npm install
npm run dev
```

Or just open `index.html` directly in a browser.

## Configuration

Edit `HUB_CONFIG` in `index.html`:

```javascript
const HUB_CONFIG = {
  brevo_form_url: '{{BREVO_FORM_URL}}',        // Your Brevo form URL
  stripe_checkout_link: '{{STRIPE_CHECKOUT}}',  // Stripe Checkout link
  beast_api_base: 'https://saturno-beast-api.vercel.app'
};
```

## Bonus Vault Items

Edit `data/bonus_vault_items.json` to add/remove items:

```json
{
  "id": "BV_XXX",
  "title": "Item Title",
  "item_type": "pdf|tool|music|course|bundle",
  "status": "ready|wip|idea",
  "owner": "Gabo Saturno",
  "origin": "original|licensed",
  "category": "calisthenics|writing|music|mindset",
  "access_level": "free|email_gate|paid_only",
  "path_or_url": "https://..."
}
```

## Features

### Movement Studio (DAW-style)
- Transport controls (play/pause/stop/record)
- BPM-synced timeline with playhead
- Drag & drop movements to timeline
- Resizable clips
- Mixer with knobs and faders
- Web MIDI support

### Bonus Vault
- Grid view of all assets
- Filter by type (PDFs, Tools, Courses, Music)
- Access level badges
- Founding Wave CTA

### Ecosystem Navigation
- Titan Forge (Linguistic Console)
- Apoapsis Writer
- Solar System (Movement Galaxy)
- Triton Onboarding
- TOC Editor
- Command Center

## BEAST API

All AI calls route through BEAST API:

```javascript
await transformWithBeast(text, 'Teacher');
```

Endpoints:
- `/api/health` - Health check
- `/api/transform` - Text synthesis
- `/api/capture` - Content capture
- `/api/sessions` - Session management

## File Structure

```
saturno-hub-starter/
├── index.html           # Main app
├── data/
│   ├── bonus_vault_items.json
│   └── schemas/
├── music/               # Local music files
├── scripts/
│   └── importers/
└── README_MVP_HUB.md
```

## Deployment

Push to GitHub and connect to Vercel/Netlify, or use GitHub Pages.

---

**Creator:** Gabo Saturno  
**Stack:** Vanilla JS + CSS + BEAST API  
**Status:** MVP - Shipping Feb 2026
