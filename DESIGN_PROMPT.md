# Design prompt — Penny marketing + legal site

The prompt used with Claude (design) to generate this site, kept so the design can be
regenerated or extended consistently. Claude had access to the Penny **app** design as
context; this prompt extends that visual language to the web.

Brand tokens live in `penny.css` (`:root` + `prefers-color-scheme` dark overrides) and
mirror `src/theme/index.ts` in the app repo.

---

```
You already have the Penny app design in this project — the warm, copper-toned pet-care
tracker. I want you to design Penny's **public marketing + legal website**, extending that
exact visual language to the web. Three pages: a fun, inviting landing page, a Privacy
Policy, and a Support/FAQ page. They must feel like the same product as the app — same
warmth, same palette, same rounded friendliness — not a generic SaaS template.

## The product (for accurate copy)
Penny — tagline "Pet care, together." A shared iOS app for households to track their pets'
meals, meds, and litter/potty, so no dose is missed and no one double-feeds the dog. The
loop: one person creates a household, adds pets and care routines, invites family; everyone
logs care and gets smart, timezone-aware reminders; there's a shared activity log and full
history. Works offline (logs sync when back online).

Pricing to reflect honestly: the **free tier is a complete product for a solo caretaker** —
unlimited pets, all reminders, logging, offline sync, full history. The paid **Penny
Household** plan ($5.99/mo or $39.99/yr — yearly is the hero, with a $29.99 first-year
intro price) unlocks the *shared* household: inviting family members, roles, and updates
when someone logs a task, plus future premium features. **Joiners never pay** — only the
owner subscribes and it covers everyone.

## Brand system — match the app exactly
Aesthetic: warm, cozy, "copper." Think a warm kitchen where a family coordinates care —
NOT a clinical medical dashboard. Cream paper, terracotta accents, filled rounded glyphs
(paw, bowl, pill, litter), generous rounded corners, soft shadows. Friendly, calm, a little
playful.

Light mode: background #FBF6EE, cards #FFFFFF, ink #2E2A24, soft/secondary ink #857B6D.
Primary accent copper #C77A3C (tint #F7E8D8, deep #A85F28, ink #8A4A1E).
Dark mode: background #171411, cards #241F19, ink #F2EBE0, soft ink #A89B89, copper #ECAB6C.
Category accent colors, used sparingly as playful highlights (e.g. feature icons): Meals
amber #E0962F, Meds red #C84B38, Cleanup teal-green #3F9E84, success green #2E7D4F.
Support BOTH light and dark via prefers-color-scheme.

Type: a friendly rounded display face for headings (Fredoka / Baloo 2 / Nunito family) and
a clean humanist sans for body (Mulish / DM Sans / Nunito) — the same fonts as the app
design. Large radii (cards ~24px, pill/rounded buttons), warm borders, soft shadows. Use
filled SVG glyphs, never thin line icons.

Voice: warm, plainspoken, a touch playful. Use real product language — "so no one
double-feeds the dog," "never miss a dose." No corporate fluff, no fake urgency, no
buzzwords.

## Page 1 — Landing page (make it fun and inviting)
Sections, in order:
1. Hero: paw/logo, "Pet care, together.", a one-line value prop, an App Store download
   badge (placeholder link), and a friendly hero visual — reuse the app's Today screen in a
   phone frame, or illustrated pets. Warm copper gradient wash is welcome.
2. The relatable problem: the "wait, did someone already feed her?" / double-dose moment.
3. How it works — three simple steps: create a household → add pets & routines → everyone
   logs, with reminders that know your timezone.
4. Features grid (with playful category-colored glyphs): shared household, meals/meds/litter
   tracking, smart reminders, offline-safe logging (a lost dose log is unacceptable), shared
   care history & activity feed, roles for family members.
5. Free vs. Penny Household — an honest, friendly pricing comparison; yearly as the hero;
   spell out "joiners never pay."
6. A short FAQ teaser that links to the Support page.
7. Footer: Penny, the tagline, links to Support and Privacy, and contact
   penny@pennytracker.pet.

## Page 2 — Privacy Policy (lay out this REAL content; do not invent legal terms)
Title "Privacy Policy," last updated July 14, 2026. Warm but readable long-form layout
(good typography, section headings, a clean data table). Cover exactly:
- Intro: Penny is a shared pet-care tracker; we do NOT sell data, do NOT use it for ads, do
  NOT track across other apps.
- Data we collect: (a) Account — email, display name, and Apple/Google sign-in identifiers;
  passwords handled by our auth provider, never seen by us. (b) Household — name, members,
  roles, invite codes. (c) Pets & care — pet names, species, birthdates, notes, photos; care
  routines (meals/meds/litter); medication name/dosage/form; a log of completed tasks
  including who and when. (d) Photos — pet and member photos you upload (optional). (e)
  Notifications — a device push token, notification preferences, and household time zone. (f)
  Subscription — subscription status/entitlement from Apple and our subscription manager; we
  NEVER receive or store card/payment details (Apple handles payment). (g) Diagnostics —
  crash reports and technical data (device model, OS version, app state at crash), used only
  to fix bugs.
- What we do NOT collect: advertising identifiers, precise location (only a timezone name),
  contacts, browsing history, or payment card details.
- Service providers (process data only on our behalf): Supabase (database, auth, photo
  storage), Apple (Sign in with Apple, in-app purchases), Google (Sign in with Google),
  RevenueCat (subscription status), Expo (push delivery), Sentry (crash diagnostics), Resend
  (essential account email).
- Sharing within your household: pets, routines, and the care log (with your name on tasks
  you complete) are visible to household members; members are added only on admin approval.
- Retention & deletion: kept while the account is active; delete via Me → profile → Delete
  account, or email us. Care-log history is preserved for the household.
- Security: HTTPS/TLS in transit; database-level access control so only household members can
  read household data.
- Children: not directed to under-13; we don't knowingly collect their data.
- Your rights: access/correct/export/delete; most doable in-app or by email.
- Changes: we update the date and, where appropriate, notify in-app.
- Contact: penny@pennytracker.pet.

## Page 3 — Support / FAQ (real content)
Title "Support." A friendly contact card with penny@pennytracker.pet (note: including device
model + iOS version speeds up help). Then an FAQ (collapsible sections) covering: how
households work; what's free vs. the Penny Household plan; how to invite someone (requires an
active plan); what happens if a subscription lapses (Apple grace → 14-day in-app grace →
household "pauses" for members, owner keeps full access, all data preserved and restored on
renewal); how to manage/cancel a subscription (through Apple, Settings → Apple ID →
Subscriptions); how to restore purchases on a new device; troubleshooting notifications
(enable in iOS Settings and in Me → Reminders; reminders fire in the household timezone); how
to reset password / change email (Forgot password? for a code; Me → profile → Email); how to
delete an account (Me → profile → Delete account).

## Constraints
- Responsive, mobile-first. The page body must never scroll horizontally; wide tables scroll
  inside their own container.
- Light and dark mode via prefers-color-scheme.
- The final host is GitHub Pages, so linking Google Fonts is fine; otherwise inline
  everything and provide a system-font fallback.
- Build as separate pages that resolve at clean routes: / (index.html), /privacy
  (privacy/index.html), /support (support/index.html). Cross-link them in headers/footers.
- Do NOT fabricate testimonials, download counts, awards, star ratings, or a company mailing
  address. Keep the privacy and support content factually to what I gave you above.

Deliver the three pages as cohesive, ready-to-host HTML.
```

---

## Notes for future regeneration

- Keep the privacy/support **content** factually accurate — it must match the App Privacy
  label in App Store Connect. Don't let a design pass rewrite the data categories or the
  subprocessor list.
- Never add testimonials, download counts, or star ratings — fabricated social proof is an
  App Review liability.
- Outstanding TODO in `index.html`: the App Store badge links to `#` in two places (hero +
  closing CTA). Swap in the real App Store URL once the app is published.
