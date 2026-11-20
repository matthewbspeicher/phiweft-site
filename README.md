# PhiWeft site

First version of the PhiWeft one-page site. Plain static files: HTML, one stylesheet, no JavaScript, no build step, no backend.

**Status: private draft for review. Not published, no domain connected.**

## Layout

```
public/            everything a web server needs; copy this folder as-is
  index.html       the page and its copy
  css/site.css     all styles (palette and spacing tokens at the top)
  fonts/           Archivo variable font (Latin, Latin Extended) and its license
  favicon.svg      weave mark
  robots.txt       blocks all crawlers while the site is in review
README.md          this file (not served)
```

All links inside `public/` are relative, so the folder works from any path or host.

The page makes no third-party requests. The Archivo typeface is self-hosted in `public/fonts/` under the SIL Open Font License (`public/fonts/OFL.txt`); the files came from Google Fonts (Archivo v25).

## Preview locally

```bash
python3 -m http.server 4173 --bind 127.0.0.1 --directory public
```

Then open http://localhost:4173. The server listens on this machine only.

## Review copy on Linode, behind a login

Nothing here deploys itself. To put a review copy on a Linode:

1. Copy `public/` to the server, for example to `/var/www/phiweft-review/`.
2. Serve it from a host name that is not the real domain, over HTTPS.
3. Require a login for the whole site with HTTP basic auth. In nginx:

   ```nginx
   location / {
       auth_basic           "PhiWeft review";
       auth_basic_user_file /etc/nginx/phiweft-review.htpasswd;
       add_header           X-Robots-Tag "noindex, nofollow" always;
   }
   ```

   Create the password file on the server with `htpasswd -c /etc/nginx/phiweft-review.htpasswd <reviewer>`. Keep it outside `public/` and out of version control.

Basic auth sends the password with every request, so only use it over HTTPS.

`robots.txt` and the `noindex` tag only ask crawlers to stay away. They do not make the site private; the login does.

## Before publishing

These are deliberate draft markers. Remove or replace each one at launch:

- The dark "Private draft for review" strip at the top of `index.html`.
- `<meta name="robots" content="noindex, nofollow">` in `index.html`, and the blanket `Disallow` in `robots.txt`.
- "(draft)" in the page title.
- The contact placeholder box: needs a confirmed contact method. The "Discuss an integration" button points at this section.
- The footer placeholder: needs the approved business name and details.
- Founder and service claims in the copy: confirm each is cleared to publish.
