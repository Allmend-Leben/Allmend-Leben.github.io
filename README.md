# Allmend Bern — Outer Post (öffentliche Webseite)

Die öffentliche Seite der Initiativgruppe für Ansprache und Kommunikation. Gebaut mit **Hugo** und dem **Venture-Standard-Theme** (`themes/venture/`) — der erste Abzug des cloudsters Venture-Standards.

## Inhalte pflegen (ohne Technik)

Alle Inhalte sind **Markdown-Dateien** unter `content/`. Eine Datei ändern = die Seite ändern.

| Was | Wo |
|---|---|
| Startseite (Hero, Kacheln) | `content/_index.md` |
| Die Idee · Wie wir leben · Mitmachen · Kontakt | `content/<bereich>/_index.md` |
| Wissens-Artikel | `content/wissen/<name>.md` |
| **Neuer Blog-Beitrag / Termin** | neue Datei `content/aktuelles/JJJJ-MM-TT-titel.md` |

Ein neuer Beitrag braucht oben nur diesen Kopf:

```markdown
---
title: "Überschrift"
lead: "Ein Satz Vorschau."
date: 2026-10-03
---

Der Text …
```

## Lokal ansehen

```bash
hugo server
```

Dann `http://localhost:1313` öffnen. (Hugo installieren: <https://gohugo.io/installation/>.)

## Veröffentlichen

Statischer Build nach `public/`:

```bash
hugo --minify
```

Deployment über **Cloudflare Pages** (Build-Command `hugo --minify`, Output `public`). Domain wird eingehängt, sobald sie feststeht — die Seite selbst ist domain-agnostisch.

## Eigenständig & host-neutral

Dies ist ein **in sich geschlossenes Hugo-Projekt** (Repo-Wurzel = Site-Wurzel) — bewusst so, damit es auf **jedem** Host läuft und Provider- wie Sichtbarkeits-Wahl offen bleiben. Deploy-Rezepte (GitHub Pages · Cloudflare · Netlify), Domain-Anbindung und der Öffentlich-↔-Privat-Schalter stehen in [`DEPLOY.md`](DEPLOY.md).

## Verankerung in der Instance

Die Außenseite ist die **öffentliche Membran** des Commons: als **eigenes Repo** geführt und über ein **Git-Submodul** unter `instance/portals/extranet/` in der (privaten) `.o`-Instance verankert. So bleibt der Inhalt in der Instance referenziert (*Commons as Code*, ein Dach) — und ist zugleich frei hostbar. Der private Kern und die öffentliche Seite bleiben sauber getrennt.
