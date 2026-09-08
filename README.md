# kingfisher-data

Public data-only mirror for the Kingfisher project. The application
source lives in [mardakurt/kingfisher](https://github.com/mardakurt/kingfisher);
this repository is the home of:

- the **public landing page** for Kingfisher
  (served at <https://mardakurt.github.io/kingfisher-data/>);
- the **optional reference packs** the application installs on demand
  (Elite OTB, Recent Theory, High-Rated Online).

## Contents

| Path                   | What it is                                          |
| ---------------------- | --------------------------------------------------- |
| `index.html`           | Public landing page (the marketing site)            |
| `assets/`              | Static assets for the landing page                  |
| `manifest.webmanifest` | Web app manifest for the landing page               |
| `robots.txt`           | Crawler policy                                      |
| `reference-elite-v2/`  | Elite OTB reference pack (Lichess broadcast, 2020+) |
| `reference-recent-v1/` | Recent Theory reference pack (last two years)       |
| `reference-online-v1/` | High-Rated Online reference pack (2400+ Lichess)    |

The three `reference-*` directories each contain a `manifest.json` and
the chunk files the manifest points to. The application fetches them
directly from the GitHub Pages site served from this repository:

- <https://mardakurt.github.io/kingfisher-data/reference-elite-v2/manifest.json>
- <https://mardakurt.github.io/kingfisher-data/reference-recent-v1/manifest.json>
- <https://mardakurt.github.io/kingfisher-data/reference-online-v1/manifest.json>

GitHub Releases are an archival fallback. GitHub Pages is the live
source because release-download redirects do not supply the browser CORS
permission the application needs.

## Licence

- The data itself is published under the licence declared in each
  manifest:
  - Elite OTB and Recent Theory: CC BY-SA 4.0
  - High-Rated Online: CC0 1.0
- The landing page source is part of the Kingfisher project licence in
  the main repository.

## Deploying a new pack version

1. Build the pack locally with
   `npm run reference:build -- --id <pack-id>` in the main repository.
2. Verify the manifest, the chunk digests, and the install against a
   clean profile.
3. Add a new directory here (e.g. `reference-elite-v3/`) containing
   the manifest and the chunks. Older version directories are
   retained for archival download.
4. Commit and push.
5. The Pages site picks up the new directory on the next deploy.

## Deploying a new landing page

The landing page is the static `index.html` and the `assets/`
directory. Edit, commit, push. GitHub Pages serves the new version on
its next deploy.
