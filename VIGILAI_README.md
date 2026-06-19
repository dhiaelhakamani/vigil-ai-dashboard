# VIGIL·AI — Search & Rescue Surveillance Dashboard

## Overview
VIGIL·AI is a surveillance dashboard for a Raspberry Pi 5 + YOLOv8-powered search and rescue robot. It provides a live camera feed, real-time detection logging, and situational awareness tools.

## Tech Stack
- Pure HTML/CSS/JS — no build step, no frameworks, no dependencies
- GitHub Pages for hosting
- Web Audio API for alert sounds

## Repository
- **GitHub:** https://github.com/dhiaelhakamani/vigil-ai-dashboard
- **Live:** https://dhiaelhakamani.github.io/vigil-ai-dashboard/index.html

## Files
| File | Purpose |
|------|---------|
| `index.html` | Login page (authentication gate) |
| `dashboard.html` | Main dashboard (video feed, detections, telemetry, settings) |
| `vigilailogo.png` | Logo used on dashboard header |
| `vigilogo_notext.png` | Logo used on login page (no text variant) |
| `.nojekyll` | Required for GitHub Pages static hosting |

## Credentials (hardcoded)
| Username | Password |
|----------|----------|
| `amanidhiaelhak` | `15112003` |
| `fennourlyes` | `08122003` |
| `admin` | `admin` |

## Dashboard Features

### Video Feed
- Left panel: Live MJPEG stream from `/video_feed`
- Fullscreen button (cyan icon next to LIVE badge)
- Scanline overlay and corner brackets for surveillance aesthetic
- Stream offline fallback state
- Keyboard shortcut: `F` to toggle fullscreen

### Detections Panel
- Right panel: Logs fetched from `/detections` API endpoint
- Cards with thumbnail, type label (FIRE/PERSON/VEHICLE/OBJECT), and timestamp
- NEW tag animation on fresh detections (fades after 3s)
- Click card to open lightbox with full-size image
- Keyboard shortcut: `E` to export CSV

### Stats Summary Bar
- Below detections toolbar
- Shows colored dots with counts per type (FIRE/PERSON/VEHICLE/OBJECT)
- Updates automatically on each refresh

### Telemetry Panel
- In video meta bar: Battery %, Signal strength (dBm), Temperature (°C)
- Values simulated (drift every 3s)
- Color-coded indicators: green > yellow > red based on thresholds

### Settings Modal
- Gear icon in header opens settings
- **Refresh Interval** slider (1s–10s, default 4s)
- **Alert Sound** toggle (on/off)
- **Alert on detection type** checkboxes (default: FIRE + PERSON)

### Alert Sound
- Plays a beep (880→660Hz sine wave, 300ms) when new detections of alert-enabled types arrive
- Uses Web Audio API — no audio file needed

### Export CSV
- Button in detections toolbar
- Downloads `vigil-ai-detections_YYYY-MM-DD.csv` with columns: time, type, image
- Keyboard shortcut: `E`

### Keyboard Shortcuts
| Key | Action |
|-----|--------|
| `F` | Toggle fullscreen video |
| `R` | Force refresh detections |
| `E` | Export CSV |

## Login Page Features
- Animated grid background with drift effect
- Ambient glow pulse on card border
- Operator ID and Access Code fields with SVG icons
- Eye toggle for password visibility (red icon)
- Loading state on login button (spinner + "AUTHENTICATING..." text, 600ms delay)
- Shake animation on wrong credentials
- Attempt counter ("Failed attempt 2", "Failed attempt 3", etc.)
- Error message auto-hides after 3s

## Changelog (all modifications made)

### Initial setup
- `ba7c877` — Initial commit: dashboard with login
- `7384a6a` — Separate login page from dashboard with redirect
- `e54e211` — Add second user: fennourlyes
- `9ac9145` — Add logout button to dashboard
- `e50ec22` — Fix username: amanidhiaelhakamani → amanidhiaelhak; add admin/admin
- `5c46af6` — Add .nojekyll for GitHub Pages deployment

### Logo changes
- `3d3980a` — Replace LOGO.png with vigilailogo.png on both pages
- `f08e17d` — Fix login page logo sizing
- `74623b5` — Enlarge login page logo to 72px
- `a54ca5c` — Enlarge login page logo to 120px
- `077a6da` — Switch login page to vigilogo_notext.png
- `61c873c` — Track vigilogo_notext.png in git (was missing)
- `2fa1f9e` — Resize login logo to 90px

### Dashboard features
- `e5ab377` — Add settings modal (refresh interval, alert sound toggle, alert type checkboxes), alert sound (Web Audio API), and CSV export
- `919ded7` — Add fullscreen toggle for video feed
- `ec670b0` — Make fullscreen button more visible (accent color)
- `c7eba8a` — Add stats summary bar (colored dots with counts), battery telemetry panel (battery/signal/temp), keyboard shortcuts (F/R/E)
- `a657bd0` — Mobile responsive adjustments (header, telemetry, stats bar, toolbar)

### Login page enhancements
- `46e0bb8` — Add shake animation, loading state, password visibility toggle, ambient glow, attempt counter
- `25b20fd` — Increase pw toggle hit area, fix cursor
- `9310efd` — Style pw toggle red, adjust position
- `5f9f388` — Fix pw toggle visibility color

### Layout fixes
- `97725b5` — Remove fixed 80vh on detections scroll, use flex for full-viewport fit
- `bd5e092` — Constrain main grid to viewport height, reduce video min-height
