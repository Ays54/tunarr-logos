# tunarr-logos

Publicly-hosted channel assets for my self-hosted **Tunarr** IPTV setup, served over HTTPS so **Plex Live TV clients can load them from anywhere** — including remote viewers on a different network.

## Why this repo exists

Plex clients fetch a channel's logo from whatever URL sits in the channel's `icon.path` (Tunarr passes it through verbatim into the M3U `tvg-logo` and the XMLTV `<icon src>`).

- A **container-local** path (`/images/uploads/x.png`) has no host — nothing can fetch it.
- A **LAN** URL (`http://192.168.68.50:8000/...`) only resolves on my home network.

So assets must live on a **public HTTPS host** for remote Plex clients to render them. These are deliberately public channel logos — display art, not private data. All actual media stays on my own hardware.

## Two asset types

| Dir | Size | Used for | Notes |
|---|---|---|---|
| `logos/` | 1000x1000 | Plex **guide tile** (`icon.path`) | Solid backgrounds are fine and preferred here — Plex renders them in a tile beside the channel name |
| `watermarks/` | 1200x300, **transparent** | On-video **bug** (`watermark.url`) | Must be transparent — it floats over arbitrary live video |

Tunarr keeps these in **two separate fields per channel**. The icon never appears over video and the watermark never appears in the guide — set both.

## Channels

| # | Channel | Icon | Watermark |
|---|---|---|---|
| 1 | The Guide | `logos/the-guide.png` | `watermarks/the-guide.png` |
| 2 | Cosmos Network | `logos/cosmos-network.png` | `watermarks/cosmos-network.png` |
| 3 | The Crypt | `logos/the-crypt.png` | `watermarks/the-crypt.png` |
| 4 | Kids Movie Club | `logos/kids-movie-club.png` | `watermarks/kids-movie-club.png` |
| 5 | Kids Corner TV | `logos/kids-corner-tv.png` | `watermarks/kids-corner-tv.png` |
| 6 | Chris TV | `logos/chris-tv.png` | `watermarks/chris-tv.png` |
| 7 | Adrenaline Central | `logos/adrenaline-central.png` | `watermarks/adrenaline-central.png` |
| 8 | The Laugh Factory | `logos/the-laugh-factory.png` | `watermarks/the-laugh-factory.png` |
| 9 | Family Movie Night | `logos/family-movie-night.png` | `watermarks/family-movie-night.png` |
| 10 | Pupflix | `logos/pupflix.png` | `watermarks/pupflix.png` |
| 11 | Turkey Swim | `logos/turkey-swim.png` | `watermarks/turkey-swim.png` |
| 12 | Horizon | `logos/horizon.png` | _pending_ |
| 13 | Neon | `logos/neon.png` | _pending_ |
| 14 | Fable | `logos/fable.png` | _pending_ |
| 15 | Vanguard | `logos/vanguard.png` | _pending_ |
| 16 | Heartline | `logos/heartline.png` | _pending_ |
| 17 | Second Date | `logos/second-date.png` | _pending_ |
| 19 | Sitcom Central | `logos/sitcom-central.png` | _pending_ |
| 20 | Fresh Print | `logos/fresh-print.png` | _pending_ |
| 21 | The Knee Slap | `logos/the-knee-slap.png` | _pending_ |


## URL pattern

```
https://ays54.github.io/tunarr-logos/logos/<name>.png
https://ays54.github.io/tunarr-logos/watermarks/<name>.png
```

## Adding or replacing an asset

1. Name it in **lowercase kebab-case** (`the-laugh-factory.png`) so the public URL stays readable.
2. Commit + push. GitHub Pages publishes within ~a minute.
3. Point Tunarr at the new URL via its API (or the admin UI).
4. **Use a new filename when replacing art** — Plex clients cache thumbs by URL, and a fresh name is the cheapest cache-bust.

## Watermark tuning

`watermark.width` is a percentage of frame width: `10` = 10% (≈192px on 1080p). Short bold marks read fine at 10-12%; multi-word or decorative marks need a larger width to stay legible. Start ~14% and adjust per channel.
