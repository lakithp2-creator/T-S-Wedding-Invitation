# Thisaru & Sanjana — Wedding Website Guide

This folder is a complete, ready-to-deploy website. Everything below can be done
without writing any code — just replacing files and small bits of text.

```
site/
├── index.html          <- the whole website (open this in a text editor)
├── GUIDE.md             <- this file
└── images/
    ├── couple.jpg        <- main hero photo
    ├── groom.jpg          <- Thisaru's contact avatar
    ├── bride.jpg           <- Sanjana's contact avatar
    ├── hotel.jpg            <- venue photo
    ├── gallery-v1.jpg        <- gallery: vertical photo 1
    ├── gallery-v2.jpg         <- gallery: vertical photo 2
    ├── gallery-v3.jpg          <- gallery: vertical photo 3
    ├── gallery-sq1.jpg          <- gallery: square photo 1
    ├── gallery-sq2.jpg           <- gallery: square photo 2
    ├── gallery-sq3.jpg            <- gallery: square photo 3
    ├── gallery-sq4.jpg             <- gallery: square photo 4
    ├── gallery-sq5.jpg              <- gallery: square photo 5
    └── gallery-sq6.jpg               <- gallery: square photo 6
└── audio/
    └── song.mp3           <- background music
```

---

## 1. Changing images

To swap any photo, just **replace the file with your own photo using the exact
same file name** (e.g. save your new venue photo as `hotel.jpg` and overwrite
the one in `images/`). Keep the same `.jpg` extension. That's it — no need to
touch `index.html` at all.

Tips:
- `couple.jpg` and the gallery photos look best around 1000–1500px on the
  longer side — no need for huge multi-MB camera originals.
- `groom.jpg` / `bride.jpg` / `gallery-sq*.jpg` are shown as squares — a
  roughly square crop looks best.
- `gallery-v*.jpg` are shown tall (portrait) — a portrait or vertical crop
  looks best.
- If you'd rather use different file names, you can — just also update the
  matching `src="images/....jpg"` in `index.html` (search for the old name).

---

## 2. Changing phone numbers

The page only shows a "WhatsApp" button for each contact (no phone number
printed on the page). Open `index.html` in any text editor and search for
`wa.me/9477` — you'll land on the two WhatsApp links (one for Thisaru, one
for Sanjana), e.g.:
```html
<a href="https://wa.me/94771234567" ...>
```
This number must be in international format **with no `+`, spaces, or
leading `0`** — e.g. a Sri Lankan number `077 123 4567` becomes
`94771234567`.

Search for `wa.me/9477` to jump straight to both links.

---

## 3. Background music

The site plays `audio/song.mp3`, starting the moment a guest taps the
envelope, and loops for as long as they stay on the page. The bottom-right
button lets them mute/unmute it.

**To adjust the volume:** open `index.html`, search for `MUSIC_VOLUME`
(near the top of the `<script>` at the bottom of the file) — you'll see:
```js
var MUSIC_VOLUME = 0.35;
```
Change `0.35` to any number between `0` (silent) and `1` (full volume),
save, and re-deploy.

**To swap the track:** just replace `audio/song.mp3` with a different file
**using the exact same file name** (`song.mp3`) — no code changes needed. If
you'd rather use a different file name or format (e.g. `.wav`), update the
`src="audio/song.mp3"` in the `<audio>` tag near the top of `<body>` to match.

Make sure any music you use is one you have the rights to put on a public
website — a royalty-free track, one you created, or one you're properly
licensed for.

---

## 4. Publishing it online (Vercel)

Vercel hosts static sites like this one for free and gives you a public
`https://your-name.vercel.app` link anyone can open.

**Easiest method — no coding tools needed:**

1. Go to **vercel.com** and sign up (GitHub, GitLab, or email all work).
2. Once logged in, click **Add New… → Project**.
3. Choose **"Deploy without Git"** / drag-and-drop (Vercel shows a drop zone
   for a folder or zip on the new-project screen).
4. Drag this whole `site` folder (or the zip you were given) into that drop
   zone.
5. Leave the settings as default (it's a static site — no build command
   needed) and click **Deploy**.
6. After a few seconds you'll get a live link like
   `https://thisaru-sanjana.vercel.app` — that's the link you share with
   guests.
7. Whenever you edit a photo, a number, or the music, just re-upload the
   folder the same way (drag-and-drop again) to publish the update — Vercel
   will replace the live site with your new version, same link.

**Alternative (if you're comfortable with GitHub):**
1. Push this folder to a new GitHub repository.
2. On vercel.com, click **Add New… → Project → Import Git Repository** and
   pick that repo.
3. Vercel deploys it automatically, and redeploys every time you push a
   change — no manual re-upload needed.

That's it — once deployed, the link works for anyone, on any device, with no
sign-in required.
