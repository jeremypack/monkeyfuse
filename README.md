# monkeyfuse.com

The Monkeyfuse company website. Static HTML and one stylesheet, hosted on GitHub
Pages at [monkeyfuse.com](https://monkeyfuse.com).

No build step, no framework, no dependencies. No webfonts, analytics, or
third-party scripts of any kind — which is both a performance decision and a
consistency one, given what the privacy policy promises.

## Structure

```
index.html           Home — company, MasterMeals, approach, contact
contact.html         Contact details, support, data requests
privacy.html         Privacy policy (required by the App Store)
terms.html           Terms of service
404.html             Not-found page (served automatically by GitHub Pages)
robots.txt           Crawler policy
sitemap.xml          Sitemap
CNAME                Custom domain for GitHub Pages
assets/css/site.css  All styles for every page
assets/img/          Favicon, touch icon, social share image
```

## Local development

The pages use root-relative paths (`/assets/...`), so opening `index.html`
directly from the filesystem will not load the stylesheet. Serve the directory
instead:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Making changes

**Styles.** Everything lives in `assets/css/site.css`. Colours, spacing, and
type sizes are CSS custom properties defined in the `:root` block at the top —
change a token there and it updates across every page. Dark mode is handled by
the `prefers-color-scheme` block immediately below it; if you add a colour, add
its dark counterpart at the same time.

**Page shell.** The header, footer, and `<head>` metadata are duplicated in each
HTML file, since there is no template step. If you change navigation links or
metadata, change them in all five pages. Each page sets `aria-current="page"` on
its own nav item.

**Legal pages.** The "Last updated" dates in `privacy.html` and `terms.html` are
hardcoded in a `<time>` element. Update them by hand when the policy actually
changes — they must not be generated from the current date, or the pages would
claim to have been revised every time someone loads them.

**Social share image.** `assets/img/og.png` is a 1200×630 PNG referenced by the
`og:image` tags. Its source is `assets/img/og-source.html`. To regenerate after
editing that file:

```bash
cd assets/img && "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless --disable-gpu --hide-scrollbars --screenshot=og.png --window-size=1200,630 "file://$PWD/og-source.html"
```

## Deployment

Pushing to `main` publishes the site. GitHub Pages serves from the repository
root; `CNAME` pins the custom domain and must not be deleted.

## DNS

The apex domain points at GitHub Pages via A records:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

Optionally, a `CNAME` record for `www` pointing at `monkeyfuse.github.io`.
Providers that support CNAME flattening (Cloudflare, for example) can use a
CNAME at the apex instead of the A records.

These addresses change occasionally — check
[GitHub's apex domain documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain)
before troubleshooting. In repository **Settings → Pages**, the custom domain
should be `monkeyfuse.com` with **Enforce HTTPS** enabled.

## Contact

hello@monkeyfuse.com
