# ADR-001 — Web-Presence-Standard für Ventures

**Status:** vorgeschlagen · **Datum:** 2026-08-05 · **Kontext-Ebene:** cloudsters (venture-übergreifend)

## Kontext

Für Web-Präsenzen sind bisher zwei divergierende Wege entstanden, ohne Regel, wann welcher gilt:

- **`commons.engineering`** — Hugo + Cloudflare Pages + Pagefind. Content als Markdown, keine `node_modules`, sehr wartungsarm.
- **`cloudsters.net`** — Astro + Tailwind + React + MDX auf Cloudflare Pages. Volle Design-/App-Tiefe, aber eine echte Node-Toolchain (~16.700 Dateien im `node_modules`), die gepflegt werden muss.

Anlass ist die **Outer-Post-Seite für Allmend Bern**: eine dauerhafte, blog-fähige Seite, gepflegt von einer nicht-technischen Gruppe, die als Muster für weitere überschaubare Ventures dienen soll.

## Entscheidung

Ein **Drei-Stufen-Standard**:

| Stufe | Wann | Stack |
|---|---|---|
| One-Pager / Embed | eine statische Seite, kein Blog | Hand-HTML |
| **Venture-Standard** | dauerhafte Seite, Blog, Hintergrund-Artikel, nicht-technischer Steward, forkbar | **Hugo + `venture`-Theme + Pagefind**, hostagnostisch (GitHub Pages *oder* Cloudflare Pages) |
| Flaggschiff | Design-Tiefe, interaktive Komponenten, viele Beitragende | **Astro + Tailwind** |

**Für überschaubare Ventures — egal welcher Bereich — ist der Venture-Standard (Hugo) der Default.** Astro-Niveau bleibt den Föderations-/Framework-Flaggschiffen vorbehalten, wo die Toolchain sich rechtfertigt.

Das `venture`-Theme leitet Look & Feel 1:1 aus der Familie ab: geteiltes blaues Chrome (`#3AAADC`), Inter, Pill-CTAs, Karten — plus **ein warmer Akzent pro Venture** über `hugo.toml`-Params.

## Hosting — bewusst hostagnostisch

Der Hugo-Build ist statisch und läuft auf beiden Plattformen. Zwei gesegnete Rezepte:

| Rezept | Wann | Wie |
|---|---|---|
| **GitHub Pages** (wie das erste Commons OS, `commons-os.github.io`) | ein Vendor (GitHub), Redaktion direkt im Web-Editor, **öffentliches** Site-Repo | offizielle **Hugo-GitHub-Action** — Pages-nativ baut nur Jekyll, Hugo braucht die Action |
| **Cloudflare Pages** (wie commons.engineering, cloudsters.net) | Build aus **privatem** Instance-Repo, Inhalt bleibt in der `.o` | Repo verbinden, Root `instance/portals/extranet`, Build `hugo` |

Hinweis: `commons-os.github.io` ist **Jekyll** (Pages-nativ, erste Generation). Die späteren Familienseiten sind auf **Hugo/Astro** umgestiegen — der Venture-Standard bleibt **Hugo**; GitHub Pages tragen wir über die Hugo-Action, nicht über Jekyll.

## Konsequenzen

- **Positiv:** niedrige Wartungslast; Redaktion in Markdown; Blog/Termine/RSS/i18n von Haus aus; kohärentes Familien-Erscheinungsbild; forkbar als „stellvertretendes" Muster; Inhalt lebt in der `.o`-Instance (Commons as Code).
- **Negativ / Grenzen:** weniger Design-Freiheit als Astro; interaktive Bausteine erfordern eine bewusste Hochstufung zum Flaggschiff.
- **Herkunft & Promotion:** Das Theme wird in-place an **Allmend Bern** (erster Konsument) entwickelt und verfeinert; danach zu einem eigenständigen `cloudsters-venture-site`-Starter promoted. Bis dahin lebt der Kanon in diesem ADR + `README.md` des Themes.

## Offen

- **Hosting-Grundsatz je Venture** — die eine echte Wertentscheidung: *Inhalt-in-der-Instance (Commons as Code) → Cloudflare Pages aus dem privaten `.o`* **vs.** *ein Vendor + Web-Editing → dediziertes öffentliches Site-Repo auf GitHub Pages (commons-os-Muster)*. Für Allmend Bern noch zu wählen.
- Kanonischer Ablageort für den promoteten Starter (eigenes Repo unter der Föderation?).
- Suche (Pagefind) erst aktivieren, wenn die Inhaltsmenge es rechtfertigt.
