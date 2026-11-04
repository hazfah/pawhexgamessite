# fahey.io — static site (PawHex)

Plain HTML/CSS, no build step, no JavaScript, no cookies. Everything in this folder is the site.

## Fill in the placeholders
Find-and-replace across all files (they appear in every page's header/footer and in the PawHex and legal pages):

| Placeholder | Replace with |
|---|---|
| `[APP STORE URL]` | the App Store link (after release) |
| `[APP ID]` | the numeric App Store app ID (after release) |
| `[MIN iOS VERSION]` | minimum iOS version from the build |

The pages are written in this order: `index.html`, `games/pawhex/`, `privacy/`, `support/`, `terms/`, `credits/`, `404.html`.
Also update "Last updated" on the privacy and terms pages when their text changes.

## Publish on GitHub Pages
GitHub Pages on a free account needs a **public** repository, so put this folder in its **own new repo** (not the private game repo):

1. Create a new public repo, e.g. `pawhex-site`.
2. Copy the *contents* of this folder (not the folder itself) into the repo root and push to `main`.
3. Repo **Settings → Pages → Build and deployment**: Source = *Deploy from a branch*, Branch = `main` / `(root)`.
4. Same page, **Custom domain**: enter `fahey.io`, save, then tick **Enforce HTTPS** once the certificate is ready. (The `CNAME` file in this folder already says `fahey.io`.)

## DNS at VentraIP
In the VentraIP client area, open the domain's DNS records and add:

| Type | Name | Value |
|---|---|---|
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| CNAME | `www` | `<your-github-username>.github.io` |

(Check these against GitHub's current "Managing a custom domain for GitHub Pages" docs before saving.) Remove any older `@` A records
pointing at VentraIP parking/hosting. DNS can take from minutes to a few hours.

## Check it worked
- https://fahey.io/ loads the home page.
- https://fahey.io/app-ads.txt shows a single line of plain text: `google.com, pub-4496264940245202, DIRECT, f08c47fec0942fa0`
- https://fahey.io/privacy/ loads (use this URL in App Store Connect).

Set the App Store listing's marketing/support URLs to `https://fahey.io/games/pawhex/` and `https://fahey.io/support/`, and its
developer website to `https://fahey.io` so AdMob can find `app-ads.txt` (it can take a day or more to be picked up after release).

## Adding another game
Copy `games/pawhex/` to `games/<new-game>/`, edit it, and copy the game card in `index.html` ("All games"). Add the new URL to `sitemap.xml`.
