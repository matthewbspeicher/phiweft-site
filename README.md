# PhiWeft site

The PhiWeft one-page site. Plain static files: HTML, one stylesheet, no JavaScript, no build step, no backend, no form, no tracking.

**Status: published on 2026-11-23 at https://matthewbspeicher.github.io/phiweft-site/ from a public repository. No custom domain connected yet.**

## Layout

```
public/            everything a web server needs; copy this folder as-is
  index.html       the page and its copy
  css/site.css     all styles (palette and spacing tokens at the top)
  fonts/           Archivo variable font (Latin, Latin Extended) and its license
  img/             logo mark used in the header
  favicon-32.png, apple-touch-icon.png   browser and home-screen icons
  robots.txt       allows crawlers (launch setting)
README.md          this file (not served)
brand/logo/        logo PNGs on a transparent background, and the original image (not served)
.github/workflows/pages.yml   manual-only publish to GitHub Pages
```

All links inside `public/` are relative, so the folder works from any path or host.

The page makes no third-party requests. The Archivo typeface is self-hosted in `public/fonts/` under the SIL Open Font License (`public/fonts/OFL.txt`); the files came from Google Fonts (Archivo v25).

## Preview locally

```bash
python3 -m http.server 4173 --bind 127.0.0.1 --directory public
```

Then open http://localhost:4173. The server listens on this machine only.

## Hosting: GitHub Pages

The site is published to GitHub Pages from the `public/` folder. The repository was made public on 2026-11-23, so the plan question below no longer applies; it is kept for the record.

### Two things that were open before publishing

**1. The GitHub plan allows Pages from this private repository.**

GitHub's documentation says that if the account owning the repository is on GitHub Free, the repository must be public to use Pages, and it lists Pages in private repositories under GitHub Pro. The plan of the account that owns this repository has not been confirmed. To check:

- Sign in as the repository owner and look at the current plan in the account's billing settings (expected at https://github.com/settings/billing; that address was not checked against the docs).
- Or open the repository's Settings, then Pages. If the "Build and deployment" options are not offered there, the plan does not cover it.

Sources: https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site and https://docs.github.com/en/get-started/learning-about-github/githubs-plans

If the plan does not cover it, that is a blocker: decide between upgrading the plan and making the repository public. Do not change visibility as a side effect of publishing.

**2. The site fits GitHub's rules for Pages.**

Read https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits. The relevant rule says Pages may not be used as free hosting to run an online business, an e-commerce site, or a site primarily directed at commercial transactions or software as a service. This site is a one-page brochure with an email link: no sales, payments, accounts or hosted software. That reading suggests it fits, but the page does not mention brochure or consulting sites either way, so the call is the owner's. GitHub Support can confirm in writing if wanted. The size and traffic limits (1 GB site, 100 GB a month) are far above what this site uses.

### Publishing steps

1. In the repository settings, set Pages to build from GitHub Actions.
2. Run the "Publish to GitHub Pages" workflow by hand (`.github/workflows/pages.yml`). It only ever runs manually (first run 2026-11-23; run it again after each change to `public/`), and it refuses to publish if it finds draft markers in the page or a blanket `Disallow` in `robots.txt`.
3. Add the custom domain in the Pages settings, then point DNS at GitHub.
4. Load the live site and check the page, the fonts and the contact link.

## Launch checklist

- [x] Contact method: `matthew@phiweft.com` as a `mailto:` link. Mailbox verified by the owner: sending and replying tested in both directions.
- [x] Footer: `© 2026 PhiWeft, LLC`. No address, EIN or filing number.
- [x] Draft banner removed, "(draft)" removed from the page title.
- [x] `noindex` meta tag removed and `robots.txt` set to allow crawlers.
- [x] Example section is labeled as an illustrative scope, not past PhiWeft work. No client names, logos or third-party product material.
- [x] Owner sign-off on the copy, including the founder bio and service claims (approved 2026-11-23).
- [x] GitHub plan: no longer needed. The owner made the repository public on 2026-11-23.
- [x] GitHub Pages usage rules (see above): the owner chose to publish on 2026-11-23.
- [x] Published and checked live: page, stylesheet, fonts, icons and logo all load; nothing outside `public/` is served.
- [ ] Domain and DNS. Not started.
