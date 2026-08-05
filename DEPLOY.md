# Deployment — host-neutral

Diese Seite ist ein **eigenständiges Hugo-Projekt** (Repo-Wurzel = Site-Wurzel). Der Build ist statisch und läuft auf **jedem** Host — Provider-Wahl und Sichtbarkeit sind unabhängige, jederzeit umlegbare Schalter.

```bash
hugo --minify   # → public/
```

## Rezepte (austauschbar)

### GitHub Pages — öffentliches Repo, ein Vendor
Enthalten: `.github/workflows/deploy-pages.yml`. In den Repo-Einstellungen **Pages → Source: GitHub Actions** wählen — fertig. (Pages baut nativ nur Jekyll; Hugo läuft über diese Action.) Redaktion direkt im GitHub-Web-Editor möglich.

### Cloudflare Pages — auch aus privatem Repo
Repo verbinden · Build `hugo` · Output `public` · Env `HUGO_VERSION`. Baut private Repos gratis — der Weg, wenn das Repo privat bleiben soll ohne bezahlten Plan.

### Netlify / Vercel / statischer Webspace
Build `hugo`, Publish-Verzeichnis `public/`. Provider-Datei (`netlify.toml` o. ä.) optional und austauschbares Beiwerk — Theme & `content/` bleiben reines Hugo.

## Eigene Domain anhängen
1. Beim Host die Domain hinterlegen (GitHub: *Settings → Pages → Custom domain*; Cloudflare/Netlify analog).
2. DNS beim Registrar auf den Host zeigen (CNAME/ALIAS).
3. Bei fester Domain `baseURL` in `hugo.toml` setzen (die Pages-Action setzt sie sonst automatisch).

Bis dahin läuft die Seite auf der kostenlosen Host-URL — **domain-agnostisch**, nichts blockiert.

## Öffentlich ↔ privat umlegen
Die Struktur erzwingt nichts:

- **öffentlich** → kostenloses GitHub Pages oder jeder andere Host.
- **privat** → GitHub **Team** (Pages aus privatem Repo) **oder** Cloudflare/Netlify/Vercel (bauen private Repos gratis).

Kein Umbau — nur Sichtbarkeit + Host-Rezept wechseln.
