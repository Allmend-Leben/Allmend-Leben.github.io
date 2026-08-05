# Venture Standard — the cloudsters venture-site theme

*A low-maintenance Hugo theme for the public site (**Outer Post**) of a manageable venture — regardless of domain (Urban, Business, Life, Ecology). Its look & feel is derived 1:1 from the cloudsters family (`cloudsters.net`, `commons.engineering`): shared blue chrome, Inter type, pill CTAs, card grids — with **one warm accent per venture**.*

---

## When to use which stack — the three-tier standard

| Tier | Use when | Stack |
|---|---|---|
| **One-pager / embed** | a single static page, no blog | hand-HTML |
| **★ Venture Standard (this)** | a durable site with a blog, background articles, a **non-technical** steward, that should be **forkable** | **Hugo + this theme + Cloudflare Pages + Pagefind** |
| **Flagship** | design-system depth, interactive components, many contributors | **Astro + Tailwind** (the `cloudsters.net` pattern) |

Reach for the flagship tier only when the interactivity genuinely earns its Node toolchain. For everything "überschaubar", this theme is the default.

## Why Hugo for small ventures

- **No build toolchain** — the steward writes Markdown, nothing else. A single Hugo binary, no `node_modules`.
- **Blog, dates & RSS built in** — "Aktuelles / Termine" needs no extra machinery.
- **Multilingual-ready** (Hugo i18n) — maps the master-EN / local-language split cleanly.
- **Commons as Code** — content lives as Markdown *inside the venture's `.o` instance* (`instance/portals/extranet/`); the instance stays the source of truth.
- **Forkable** — a new venture copies this theme and writes its own `content/` + `hugo.toml`.

## What the site looks like — information architecture

The visible sections are human and warm; the **Purpose-Spiral dimensions** are the invisible spine.

| Visible section | Spine |
|---|---|
| Start | (bundles all) |
| Wer wir sind / Die Idee | D1 — Bestimmung & Identität |
| Warum jetzt | D0 — Wahrnehmung & Mandat |
| Mitmachen | D2 — Teilhabe |
| Wie wir leben / was wir bieten | D3 — Angebot & Austausch |
| Ort & Tragfähigkeit | D4 — Produktion & Resilienz |
| Hintergrund / Wissen | cross-cutting (window into the BoK) |
| Aktuelles (Blog) | D0/D2 — Kommunikation |
| Kontakt | D2 |

A venture starts by filling the "now" sections and grows into the full frame without a rebuild.

## Configure a venture (in `hugo.toml`)

```toml
title = "Allmend Bern"
[params]
  brand      = "Allmend Bern"     # nav wordmark (default: title)
  description = "…"               # meta description
  accent     = "#C98A46"          # the ONE warm accent (chrome stays family blue)
  accentTint = "#F6EEE2"          # soft accent background
  heroBg     = "#F6EEE2"          # hero band background
  footerNote = "…"
  [params.navCta]
    label = "Mitmachen"
    url   = "/mitmachen/"
```

Menus are standard Hugo `[[menu.main]]` / `[[menu.footer]]` entries.

## Home page front matter (`content/_index.md`)

The home is data-driven. Front matter keys: `hero` (`eyebrow`, `heading`, `subtitle`, `primary`, `secondary`), `steps_title` / `steps_intro` / `steps[]` (`icon`, `title`, `text`), `cards_title` / `cards[]` (`icon`, `title`, `text`, `url`, `meta`), and `cta` (`heading`, `text`, `primary`). The Markdown body renders as the centred narrative. Latest `aktuelles` posts are pulled in automatically. Icons are [Lucide](https://lucide.dev) names.

## Layouts

`_default/baseof · single · list` · `index.html` (home) · `aktuelles/list · single` (blog) · partials `head · nav · footer`. Styling: `static/css/tokens.css` (family + per-venture accent vars) and `static/css/venture.css`.

## Promotion path

Developed in-place on **Allmend Bern** (its first consumer) so it runs today; once refined, `themes/venture/` is promoted to a standalone `cloudsters-venture-site` starter that every future venture forks. See `ADR-001-venture-web-standard.md`.
