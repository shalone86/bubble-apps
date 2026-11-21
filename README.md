# Bubble apps

Four little music toys that run in your browser, made by Shalone:

| App | What it is | Play it |
|---|---|---|
| **Boba Beats** | a beat maker and sampler: loops of singing bubbles, chained into songs | [shalonely.com/boba](https://shalonely.com/boba/) |
| **Pop Pads** | a fizzy drum machine, with a bass, a chord and a lead pad in every kit | [shalonely.com/pop](https://shalonely.com/pop/) |
| **Cozy Chords** | a chord harp: tap a cocoa mug for a chord, swipe the strings to strum it | [shalonely.com/chords](https://shalonely.com/chords/) |
| **Deep Drift** | a sleepy sea of jellyfish that sing when you touch them | [shalonely.com/drift](https://shalonely.com/drift/) |

No sign-up, no ads, nothing tracked. Every sound is made by the code itself
(no recordings), and each app works offline once it is on your home screen.

## Make your own

**You can.** Everything here is free for anyone to use, change, remix, sell,
or build on, for any reason, without asking and without credit (see
[License](#license)). If you make something, I would love to see it, but you
don't owe me anything.

These apps were *vibe coded*: I described what I wanted, played with the
result on my phone, said what felt wrong, and an AI (Claude) wrote and fixed
the code. You can work the same way. You don't need to be a programmer.

### The easy way: change it with an AI

1. Click **Code → Download ZIP** on this page (or *Fork* it, if you use GitHub).
2. Give the folder of the app you like (for example `pop/`) to an AI coding
   assistant, and describe what you want in plain words: *"make the pads look
   like donuts"*, *"add a kit of kitchen sounds"*, *"let me record my own
   voice on a pad"*.
3. Try it, say what's off, repeat. That's all I did.

### Try it on your computer

Each app is a plain web page in its `web/` folder: no build step, nothing to
install. A web page that plays sound needs to be served, not just opened, so
in a terminal:

```sh
cd pop/web
python3 -m http.server 8000
```

Then open http://localhost:8000 in Chrome. Change a file, reload, hear it.

### Put it online

Upload an app's `web/` folder to any web host: GitHub Pages, Netlify,
Cloudflare Pages, itch.io (as an HTML game), or your own site. That's the
whole app. Mine run on Cloudflare: each app's `cloudflare/` folder holds the
small script that serves it at its own address (`node build.mjs`, then
`npx wrangler deploy`).

### What's where

| Folder | Inside |
|---|---|
| `boba/` | Boba Beats (its own [README](boba/README.md) explains it in depth) |
| `pop/` | Pop Pads |
| `chords/` | Cozy Chords |
| `drift/` | Deep Drift |
| each `web/` | the app itself: `index.html`, `css/`, `js/`, icons, fonts |
| each `tests/` | checks that run the app in a browser and listen to it (need Node, ffmpeg and Playwright) |
| each `tools/` | helpers, like the one that films the tutorial video |
| `tools/make-icons.mjs` | draws an app's home-screen icons from a picture |
| `ROADMAP.md` | ideas for what's next |

A few ideas that are easy to borrow:

- **Sounds made from code.** Every drum, chord and string is built from simple
  waves in the browser's Web Audio (see `pop/web/js/kits.js` or
  `chords/web/js/sound.js`), so there are no sample files and no copyright to
  worry about.
- **Apps that talk to each other.** Pop Pads can send a beat to Boba Beats or
  a groove to Cozy Chords. They share the browser's storage because they live
  on the same website.
- **Saving for a music program.** WAV, MIDI and stems exports, written in
  plain JavaScript (`*/web/js/codec/`), for Logic, Ableton, GarageBand and the like.

## License

**My code and designs here are public domain: [CC0 1.0](LICENSE).** Do
anything you like with them.

A few things are not mine, and keep their own licenses (see
[THIRD-PARTY.md](THIRD-PARTY.md)):

- the **Fredoka** font (SIL Open Font License),
- **lamejs**, the MP3 encoder in Boba Beats (LGPL).

**Not included:** my voice. The narrated tutorial videos and voice recordings
used on shalonely.com are not in this repository and are not public domain.
