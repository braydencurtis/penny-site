# Penny — public site

The marketing + legal site for **Penny** ("Pet care, together."), a shared pet-care app for
households. Live at **https://pennytracker.pet** via GitHub Pages.

These pages exist partly for App Store compliance: App Review requires a reachable privacy
policy and support URL.

| Page | URL |
| --- | --- |
| Landing | https://pennytracker.pet |
| Privacy Policy | https://pennytracker.pet/privacy |
| Support / FAQ | https://pennytracker.pet/support |

## Files

```
index.html          landing page
penny.css           shared stylesheet (all design tokens, header/footer, doc + FAQ styles)
privacy/index.html  privacy policy
support/index.html  support / FAQ
CNAME               custom domain for GitHub Pages (pennytracker.pet)
.nojekyll           serve files verbatim — skip Jekyll processing
DESIGN_PROMPT.md    the Claude design prompt that generated this site
```

Static HTML/CSS — **no JavaScript, no build step, no framework**. All internal links are
relative and directory-style (`support/`, `../privacy/`) so they work from any static host.
All icons are inline SVG; fonts load from Google Fonts.

## Local preview

```bash
python3 -m http.server 8000    # then open http://localhost:8000
```

Serve it rather than opening `index.html` directly, so the directory-style routes resolve.

## Hosting

GitHub Pages, deployed from `main` / root. DNS at Namecheap points the apex at GitHub:

- Four `A` records on `@` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
- `CNAME` on `www` → `braydencurtis.github.io`

Pushing to `main` redeploys. **Enforce HTTPS** should stay on — App Review hits the privacy URL.

## Design

Colors, fonts, and glyph language match the Penny app (`src/theme/index.ts` in the app repo).
Tokens are defined in `penny.css` `:root`, with dark-mode overrides via `prefers-color-scheme`
(no toggle — it follows the OS).

Light: `--cream #FBF6EE` (bg), `--card #FFFFFF`, `--ink #2E2A24`, `--soft #857B6D`,
`--copper #C77A3C` (brand), `--tint #F7E8D8`, `--deep #A85F28`, `--copper-ink #8A4A1E`,
`--meals #E0962F`, `--meds #C84B38`, `--clean #3F9E84`, `--good #2E7D4F`.
Dark: `--cream #171411`, `--card #241F19`, `--ink #F2EBE0`, `--soft #A89B89`, `--copper #ECAB6C`.

Type: **Baloo 2** (display/headings/buttons) + **Nunito** (body). Cards 24px radius, pill
buttons, soft warm shadows.

See `DESIGN_PROMPT.md` to regenerate or extend the design consistently.

## Content accuracy

The privacy and support copy describes Penny's **real** behavior and data practices, and must
stay consistent with the App Privacy label in App Store Connect. If the app's data collection
or subprocessors change, update `privacy/index.html` to match.

Subprocessors named: Supabase (database/auth/storage), Apple (Sign in with Apple, in-app
purchases), Google (Sign in with Google), RevenueCat (subscriptions), Expo (push), Sentry
(crash diagnostics), Resend (account email).

## TODO

- App Store badge links to `#` in `index.html` (two places: hero + closing CTA) — swap in the
  real App Store URL once the app is published.
