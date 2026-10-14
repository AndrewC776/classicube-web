# classicube-web

Self-hosted [ClassiCube](https://github.com/ClassiCube/ClassiCube) web client (singleplayer) on GitHub Pages.

## How it works

`.github/workflows/deploy.yml` runs on every push to `main`:

1. Checks out ClassiCube at the tag in `CLASSICUBE_REF`.
2. Rewrites the hardcoded `/static/` asset paths to relative ones so the game works under `/<repo>/`.
3. Compiles `ClassiCube.js` with the same Emscripten image and `emcc` flags the upstream CI uses for that tag.
4. Downloads the default texture pack and sound files from classicube.net at build time (classicube.net currently only hosts the grass sounds, so other block sounds are silent).
5. Publishes `index.html`, `ClassiCube.js` and the assets to GitHub Pages.

Upgrade the game by changing `CLASSICUBE_REF` and pushing.

## Usage

- Open the Pages URL; a world is generated and saved in the browser (IndexedDB).
- `?name=Steve` sets the in-game username (letters, digits, `_`, max 16).

## Licensing

- ClassiCube code: BSD-3-Clause, (c) UnknownShadow200. The license is published alongside the build as `LICENSE-ClassiCube.txt`.
- The texture pack and sounds are fetched from classicube.net during the build and are not stored in this repository. They include artwork derived from Minecraft Classic; rights belong to their respective owners.
- This project is not affiliated with Mojang, Microsoft or Minecraft.
