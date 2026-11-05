# StajNano website

A static site for StajNano (an unofficial companion app for a compact amp-modelling pedal), made for GitHub Pages. Plain HTML, CSS, no build step,
no scripts, no external fonts or CDNs, no analytics, no cookies and no forms. It is a **separate public repository**: the app's source lives in a
private repository and must never be copied here.

**Status: draft.** Every page has `<meta name="robots" content="noindex">` so that search engines skip it until the site is ready (see "Before it goes
live").

## Pages

```
/
├── index.html            home: what it is, features, screens, stores (coming soon), the unofficial notice
├── connect/index.html    how to connect, Auto-connect, troubleshooting
├── midi/index.html       the MIDI messages of a Bluetooth foot pedal (from the app's docs/stajnano-midi-spec.md)
├── support/index.html    contact, what to write, questions
├── privacy/index.html    privacy policy, English and Korean
├── assets/styles.css     the one stylesheet
├── assets/images/        screens of the app, icons
├── .nojekyll             GitHub Pages: serve the files as they are
└── README.md
```

The pages were first written by a small script and are now plain HTML: edit them directly. The header and footer are the same on every page, so
change them on all five.

## The images

The six app screens are drawn by the app itself with sample data (not captures of a device), by the generator in the app repository:

```bash
cd ../StajNano
./tool/flutter test tool/site/site_shots_test.dart
```

It writes `../StajNano-site/assets/images/*.png`. Run it again after the look of the app changes, or replace the files with real captures.

## 1. The GitHub repository

The site is the public repository `staJD/stajnano` (visibility **Public**: GitHub Pages on a free account needs that). It exists since 2026-11-05;
to start again from nothing:

```bash
cd /Volumes/wd1/StajNano-site
git init
git add .
git commit -m "StajNano website draft"
git branch -M main
git remote add origin https://github.com/staJD/stajnano.git
git push -u origin main
```

## 2. GitHub Pages

**Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch `main`, folder `/ (root)` → Save**, and **Enforce HTTPS**. The site is at

```
https://stajd.github.io/stajnano/
```

(StajPilot's site is set up the same way: branch `main`, root, HTTPS enforced.) Every later `git push` deploys.

## 3. Before it goes live

- Remove the `noindex` line from every page:
  `grep -rl 'name="robots" content="noindex"' . | xargs sed -i '' '/name="robots" content="noindex"/d'`
- Read the privacy policy once more and take the "Draft" notice off the page.
- Fill in the store links in the "Get the app" section of `index.html` (they say "Coming soon" now).
- Check the contact address (`mailto:` in the footer of every page and on the support page).
- Click through every link in a private window.

## 4. URLs for the stores

- **Support URL:** `https://stajd.github.io/stajnano/support/`
- **Privacy Policy URL:** `https://stajd.github.io/stajnano/privacy/`
- **Marketing / website URL:** `https://stajd.github.io/stajnano/`

## Rules

- Never put the app's source, the protocol notes, the measured catalogue, logs or release packages in this repository: it is public.
- Always say "unofficial". The site names the Nano Cortex and Neural DSP only as the device StajNano works with (user decision, 2026-11-06), never with a logo or a mark, and every page's footer carries the notice: independent and unofficial, not made or endorsed by Neural DSP, the trademark owners (Neural DSP Technologies, Kemper GmbH) and a no-warranty sentence ("as is", no guarantee that it works with every unit or firmware version). The APP itself still carries no maker's or product's name. Do not write "the only app that ...": nothing here can prove it.
- If the privacy policy changes, update its effective date.
