# qweyns — bio link

Terminal-styled personal bio-link page. Live at **https://qweyns.github.io**

No build step — it's plain HTML/CSS/JS, deployed straight from the repo root via GitHub Pages.

## Structure

```
index.html               ← the whole site (markup + styles + logic, one file)
robots.txt / sitemap.xml ← basic SEO
assets/
  fonts/  MinecraftFiveBold.otf   custom pixel font, used site-wide via @font-face
  icons/  github.png, telegram.png, discord.png   social icons (same size, pixel art)
          favicon-16/32/180/512.png, og-image.png  browser tab icon + link-preview image
          note.png                                 music-note icon used by the player
  music/  track1.mp3, track2.mp3, track3.mp3        the built-in player's playlist
```

## Editing content

Almost everything lives in two objects near the top of the `<script>` tag in `index.html`:

- **`CONFIG`** — language-independent stuff: social links/URLs, track list, the visit-counter key.
- **`I18N`** — every visible string, once per language (`en` / `ru`): roles, about text, ad copy,
  console responses, achievement titles, game labels. Add a new language by adding a new key here
  and wiring a button for it next to the existing language toggle.

The site remembers the visitor's language and sound preference in `localStorage`
(keys prefixed `qweyns_`), so there's nothing to configure per-visitor.

## Features

- Terminal boot animation → profile card, typewriter role line
- Music player (play/pause/seek/volume) for the three local tracks
- Mini-console at the bottom (`help`, `links`, `play`, …) with synthesized typing sound
- Visit counter (global via a free public counter API, falls back to a local per-device count
  if that service is ever unreachable)
- Rotating self-promo "ad" panel (closeable, swipeable on mobile)
- A couple of easter eggs: the Konami code, a `sudo` joke, and a small egg-clicking mini-game
  tied to the SmashEgg plugin — achievements pop up as toasts and persist in `localStorage`
- EN/RU language toggle and a sound mute toggle, both top-right

## Deploy

Static site. GitHub Pages → Settings → Pages → Source: **Deploy from a branch**, branch **main**,
folder **/ (root)**. `index.html` must stay at the repo root for this to work.
