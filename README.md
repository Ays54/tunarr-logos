# tunarr-logos

Publicly-hosted channel logos for my self-hosted **Tunarr** IPTV setup, served over HTTPS so **Plex Live TV clients can load them from anywhere** — including remote viewers on a different network.

## Why this repo exists

Plex clients fetch the channel logo from whatever URL is in the channel's `icon.path` (passed through to the M3U `tvg-logo` and XMLTV `<icon src>`).

- A **container-local** path (`/images/uploads/x.png`) has no host — nothing can fetch it.
- A **LAN** URL (`http://192.168.68.50:8000/...`) only resolves on my home network.

So **logos must be on a public HTTPS host** for remote Plex clients to render them. These are deliberately public channel logos — display art, not private data. All actual media stays on my own hardware.

## Logos

| # | Channel | File |
|---|---|---|
| 1 | The Guide | `logos/the_guide.png` |
| 2 | Cosmos Network | `logos/cosmos_network.png` |
| 3 | The Crypt | `logos/the_crypt.png` |
| 4 | Kids Movie Club | `logos/kids_movie_club.png` |
| 5 | Kids Corner TV | `logos/kids_corner_tv.png` |
| 6 | Chris TV | `logos/chris_tv.png` |
| 7 | Adrenaline Central | `logos/adrenaline_central.png` |
| 8 | The Laugh Factory | `logos/the_laugh_factory.png` |
| 9 | Family Movie Night | `logos/family_movie_night.png` |
| 10 | Pupflix | `logos/pupflix.png` |
| 11 | Turkey Swim | `logos/turkey_swim.png` |

## Format notes

Plex's **own** channel icons are **3:2 landscape**, not square (measured from Plex's OTT channel art: 933x622, 891x594, 966x630).

Plex scales the whole canvas into the guide tile, so a square canvas containing a wide wordmark shrinks the logo along with its empty margins. **Icons are therefore authored at 1500x1000 (exactly 3:2)** with the wordmark filling the frame. `turkey_swim.png` is intentionally 1000x1000 (a single-line `[turkey swim]` wordmark where the square framing reads better).

All logos have transparent backgrounds so the player's tile colour shows through.

## Adding a new logo

1. Export at **1500x1000**, transparent PNG, wordmark filling the frame.
2. Drop it in `logos/`, add a row to the table above.
3. Commit + push. GitHub Pages serves it within ~a minute.
4. Point Tunarr at the raw URL — in the admin UI or via the API:
   ```
   https://<user>.github.io/tunarr-logos/logos/<name>.png
   ```

## Usage

Raw URL pattern:

```
https://<user>.github.io/tunarr-logos/logos/<filename>.png
```

Served via GitHub Pages from the `main` branch root.
