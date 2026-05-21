# pb-nationals — project notes

Static marketing site for the **Veolia Pickleball National Championships**
(a Carvana PPA Tour Slam), Aug 31 – Sep 6, 2026 at Cary Tennis Park, Cary NC.
Live at https://www.pbnationals.com.

## Stack / deploy

- Plain static HTML, **Tailwind via CDN** (no build step), Oswald/Manrope/Noto
  Serif fonts, Material Symbols icons.
- Hosted on **GitHub Pages** from repo `bryce-pickleball/pb-nationals`. Asset
  paths are relative (e.g. `images/...`, `logos/...`) for the Pages subdirectory.
- No package.json, no framework. Just `*.html` + `images/` + `logos/`.
- Local preview: `npx http-server` on port 4420 (see `.claude/launch.json`,
  config name `pb-nationals`).

## Structure

- `index.html` — home: hero, key-info bar, ticket-options teaser grid,
  plan-your-visit cards, sponsors wall.
- `tickets.html` — ticket tiers + pricing grid, weekly/group callout, ticket FAQ.
- `spectators.html` — tournament info, parking & directions (embedded Google
  map), know-before-you-go, FAQ accordion. Anchors: `#info #parking #know #faqs`.
- `programming.html` — NC Programming 2026: special events, on-court programming,
  stage entertainment, and theme nights as day-badged cards. Sticky section nav.
  Anchors: `#special #oncourt #stage #theme`.
- `sponsors.html` — partner wall + why-sponsor + ways-to-partner + become-a-sponsor CTA.
- `contact.html` — department contact cards, players/volunteers strip, venue map.
- Shared nav (dropdowns + mobile hamburger JS) and footer are **duplicated**
  in each page (no includes). Edit all pages when changing nav/footer.

## Known placeholders (search `TODO`)

- Ticket prices ($45 / $95 / $250) are **illustrative** — confirm real tiers/
  pricing with PPA Tour; tickets sell through Tixr.
- Partner-logo grid slots are dashed placeholders pending confirmed sponsors.
- Contact emails (`tickets@`, `sponsorships@`, `media@`, `info@`,
  `volunteers@pbnationals.com`) are assumed — confirm real addresses.
- Spectators: schedule/field, official parking details, and bag policy TBD.
- Footer social links (`#`) and Privacy/Terms links are not yet wired.

## External links (real)

- Register to play: pickleballtournaments.com/tournaments/ppa-tour-veolia-ppa-national-championships
- Buy tickets (Tixr): tixr.com/groups/ppa/events/veolia-pickleball-national-championships-184656

## Session Log

### 2026-05-21 — Added Programming page; ticket section blocked on Tixr data

- Built `programming.html` (**NC Programming 2026**) from content Bryce provided:
  Special Events (Midday Mixers, Weekly Raffle, Poster-Making, Courtside Karaoke,
  Pros Behind the Bar), On-Court (King of the Court, Play With the Pros, Free
  Youth Clinic, Pro Clinics, Glow-in-the-Dark), Stage Entertainment (Serve &
  Sound, Autographs, Trivia, Sponsor/Player Panels), and Theme Nights (Canes,
  NC Courage, NC State — marked Potential/TBD). 17 day-badged cards.
- Wired a top-level **Programming** nav item (+ mobile menu + footer "Visit"
  column) into all 6 pages, between Spectators and Sponsors. Verified in preview.
- **Ticket section NOT yet updated to real Tixr data.** Bryce asked to "copy the
  ticket section" from the Tixr listing (event 184656), but Tixr blocks automated
  fetches (403) and the preview browser is locked to localhost, so the live
  ticket names/prices couldn't be pulled. Search confirmed: players get a free
  daily grounds pass (no championship court); championship-court access needs a
  championship-court ticket or VIP pass; days appear sold as separate Tixr events
  (saw a distinct "Sunday — Championships" listing, id 184760). **Next: get the
  exact ticket names/prices/day-links from Bryce, then rebuild tickets.html +
  homepage teaser** (open task). Current ticket cards still use placeholder tiers
  ($45/$95/$250) linking to the main Tixr event.

### 2026-05-21 — Expanded one-pager into a full multi-page site

- Rebuilt the site from a single landing page into a **5-page site** modeled on
  thecjcupbyronnelson.org's layout/functionality, per Bryce's request. Kept the
  existing **red/coral dark theme + logos** (no shift to navy/gold).
- New pages: `tickets.html`, `spectators.html`, `sponsors.html`, `contact.html`;
  `index.html` rebuilt with CJ-Cup-style sections. Featured sections requested:
  **ticket pricing grid** + **sponsors wall** (skipped news feed & newsletter).
- Added shared nav with **dropdowns** (Tickets / Spectators) + **mobile hamburger
  menu** (vanilla JS, verified working), and a richer multi-column footer.
- Added `pb-nationals` static-server entry to `/Users/bryce/Documents/.claude/launch.json`
  (http-server, port 4420).
- Verified all 5 pages in preview: load clean, no broken images, no console
  errors, responsive mobile menu works. (Mid-page screenshots render blank in
  this preview tool — used the a11y snapshot to confirm below-fold content.)
- **Not yet committed / pushed.** Changes are local only. Next: review, then
  `git add` + commit + push to publish via GitHub Pages. Fill in the `TODO`
  placeholders (pricing, sponsor logos, contact emails) as info is confirmed.
