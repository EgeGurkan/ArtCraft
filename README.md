# Craft Apps — unofficial web launcher

A single static page (`index.html`) that lists the open-source "Craft" apps and opens their
**web (WebAssembly) builds from a server you run yourself**, for example a home PC that is only
reachable over a private network such as [Tailscale](https://tailscale.com/).

This repository contains **no app code, binaries or web builds**. It is only a launcher page with
links. It is **unofficial** and **not affiliated with, sponsored or endorsed by the ArtCraft Team**
(see [Trademarks](#trademarks)).

## How it works

- `index.html` is a self-contained static page that can be hosted on GitHub Pages.
- Every app card shows an **Open** button. It opens `<server>/<app-id>/` — the web build of that
  app served by **your own server**.
- **The server address is not stored in this repository.** It is given once in the link you share
  privately, and the page then remembers it in that browser (`localStorage`) and removes it from the
  address bar:

  ```
  https://<user>.github.io/<repository>/?server=https://<machine>.<tailnet>.ts.net/<path>/
  ```

  If no address is known, the page asks for it the first time someone presses **Open**.
- Only people who can reach your server (for example members of your tailnet, or people you shared
  the machine with) can open the apps. Everyone else can see the page, but the apps will not load.
- App names, descriptions, feature lists, versions and colors are a snapshot of the public, signed
  ArtCraft Launcher catalog taken when the page was generated. Descriptions are in English as
  published; the interface can be switched between English and Turkish.

## Using it

1. Put `index.html` (and this `README.md`) in a GitHub repository and enable
   **Settings → Pages** for the default branch.
2. Share the link with `?server=` **privately** (message, password manager, …). Do not commit it
   or post it publicly.
3. To change the server later, open the link again with a new `?server=` value, or clear the site
   data for the page in the browser.

Only `https://` addresses (and `http://localhost` / `http://127.0.0.1` for local testing) are
accepted as server addresses.

### Server side (not part of this repository)

The page expects each app's official web build to be served at `<server>/<app-id>/`, for example
`<server>/photocraft/`. App ids are the lower-case names used by the publishers (`photocraft`,
`vectorcraft`, `craft-anything`, …). How you host them is up to you; use the publishers' official
releases and follow each app's `HOSTING.md` (MIME types, compression, HTTPS).

## Privacy

- No analytics, cookies, trackers or accounts. The page has no backend.
- Stored only in the visitor's own browser (`localStorage`): the server address, theme, language,
  sort order, card/table view and hidden apps.
- Requests made by the page to third parties (like any web page, these hosts can see the
  visitor's IP address; no referrer is sent):
  - app icons from `getartcraft.com`,
  - screenshots on the app detail pages from `raw.githubusercontent.com`
    (`storytold/craft-launcher-assets`),
  - fonts are the system's own; nothing else is loaded.
- Projects and files created in the apps stay in the visitor's browser storage on the visitor's
  device; nothing is uploaded by this page.

## Credits

- **Design and catalog:** based on
  [ArtCraft Launcher](https://github.com/storytold/craft-launcher) by the ArtCraft team. The
  layout, the card hover behavior and the app catalog data (names, taglines, descriptions,
  feature lists, platforms, colors) come from ArtCraft Launcher and its published catalog, used
  under the MIT License (ArtCraft Launcher is dual-licensed MIT OR Apache-2.0). See
  [Third-party notices](#third-party-notices).
- **The apps** (not included here) are made by their publishers and are open source under their
  own licenses:
  - PhotoCraft, VectorCraft, FilmCraft, LightCraft, PdfCraft, EffectCraft, AniCraft, DesignCraft,
    FigCraft, WordCraft, SoundCraft, DeckCraft, CADCraft, GridCraft, TextureCraft, MaterialCraft
    and Craft Anything — by the ArtCraft Team and contributors
    ([github.com/storytold](https://github.com/storytold)), MIT OR Apache-2.0.
  - SolidCraft — by Tangency Labs and the SolidCraft contributors
    ([tangency-labs/solidcraft](https://github.com/tangency-labs/solidcraft)), MIT OR Apache-2.0.
  - MailCraft — by UCS Care Group and the MailCraft contributors
    ([UCS-Care-Group/mailcraft](https://github.com/UCS-Care-Group/mailcraft)), MIT OR Apache-2.0.
- **App icons** are loaded at runtime from `getartcraft.com` and are not redistributed in this
  repository. They belong to their respective owners.
- **Screenshots** are loaded at runtime from
  [storytold/craft-launcher-assets](https://github.com/storytold/craft-launcher-assets) and are not
  redistributed here. Per its `ATTRIBUTION.md`, the app interfaces shown are under each app's own
  license and the artwork shown is either in the public domain or was made with the apps.
- **Social icons** (embedded in `index.html`, as used by ArtCraft Launcher):
  - X, YouTube, TikTok, Instagram, Discord, GitHub — [Simple Icons](https://simpleicons.org/),
    CC0 1.0.
  - Globe (website) — [Lucide](https://lucide.dev/), ISC License.
  - LinkedIn — [Font Awesome Free](https://fontawesome.com/) 6.7.2 by Fonticons, Inc.,
    [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) (modified: fill color and view box).
  - These logos are trademarks of their respective owners and are used only to link to the
    corresponding public accounts of the ArtCraft project.

## Trademarks

"ArtCraft", the ArtCraft wordmark and the ArtCraft mark are trademarks of the ArtCraft Team. They
are **not** covered by the open-source licenses of ArtCraft Launcher or the apps (see
`docs/brand/LICENSE-brand.txt` in
[storytold/craft-launcher](https://github.com/storytold/craft-launcher)).

- This project is **not** ArtCraft Launcher and is **not** made, sponsored, endorsed, certified or
  supported by the ArtCraft Team.
- It does **not** use the ArtCraft logo, mark or wordmark. The name "ArtCraft" appears only in plain
  text: to state that this work is based on ArtCraft Launcher, and to identify the publisher of
  each app on its card.
- App names (PhotoCraft, VectorCraft, …), their icons and the names and logos of other services are
  the property of their respective owners and are used only to identify them.
- If you fork this repository, do not put "ArtCraft" in the name, logo, icon, domain or description
  of your fork.

## License

The code written for this page is released under the **MIT License**:

```
MIT License

Copyright (c) 2026 the contributors of this repository

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

### Third-party notices

Parts of `index.html` (the app catalog data and the interface design) are derived from ArtCraft
Launcher, used under the MIT License:

```
MIT License

Copyright (c) 2026 ArtCraft Team and the ArtCraft Launcher contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

The LinkedIn icon is licensed under CC BY 4.0 (attribution above); the other embedded icons are
CC0 1.0 or ISC.

## Disclaimer

- This page is provided "as is", without warranty of any kind. It is not legal advice.
- It does not host, modify or distribute the apps. Whoever runs the server is responsible for
  obtaining the apps from their official sources and for complying with their licenses.
- Several apps are labeled by their publishers as early alpha or in development. Keep your own
  backups; use the apps' Save/Export functions to keep copies of your work on your device.
- If you are a rights holder and want something changed or removed, please open an issue.
