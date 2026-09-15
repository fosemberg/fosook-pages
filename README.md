# fosook-pages

The published build of **[Fosook](https://github.com/fosemberg/fosook)** — a
co-op 3D cooking game for phones with peer-to-peer multiplayer and no game
server.

**Play:** https://fosemberg.github.io/fosook-pages/

## What is here

Nothing is written by hand in this repository. Everything under `docs/` is
generated output, served by GitHub Pages:

```
docs/
  index.html             the game
  404.html               copy of index.html, so a deep link still lands in the game
  .nojekyll              stops Pages from dropping underscore-prefixed files
  manifest.webmanifest   installable as a home-screen app
  icon.svg
  assets/                fingerprinted JS and CSS
```

There are no images, models, fonts or audio files. The 3D scene is procedural
geometry and shaders, icons are drawn at runtime from emoji, and sound is
synthesised — the whole game is about 135 kB gzipped.

## Publishing a new build

From a checkout of the sources sitting next to this repository:

```bash
cd ../fosook
npm ci
npm run build:pages     # builds, then copies into ../fosook-pages/docs
```

Then commit the result here. Set `PAGES_DIR` to publish somewhere other than
`../fosook-pages/docs`.

## GitHub Pages settings

Source: **Deploy from a branch** → branch `main`, folder `/docs`.

The build uses relative asset paths, so it works unchanged from the repository
sub-path, from a custom domain at the root, or from a local `file://` URL.

## Playing together

One player creates a game and shares the link (or holds up the QR code); the
second opens it and sends a short code back. After that the two browsers talk
directly to each other. Nothing about the match passes through GitHub Pages or
any other server — the page here is a static file and that is all it ever is.
