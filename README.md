# Associazione Educativa Laboratorio Tecnico ODV — Sito Web

Sito statico istituzionale dell'**Associazione Educativa Laboratorio Tecnico ODV** di Ancona,
organizzazione di volontariato attiva dal 1° settembre 1985 nell'educazione dei minori,
nel sostegno alle persone con disabilità e nel volontariato.

🌐 **Online su [laboratoriotecnico.eu](https://laboratoriotecnico.eu)**

## Stack

- HTML / CSS / JS puro — **nessun framework, nessuna dipendenza npm, nessun build step**
- Tutto contenuto in `index.html`: CSS nell'unico `<style>` in `<head>`, JS nell'unico `<script>` prima di `</body>`
- Font **Nunito** serviti localmente da `/fonts/` (5 varianti TTF)
- Hosting: **GitHub Pages** (branch `main`, root `/`), dominio personalizzato via `CNAME`
- Analytics: **Cloudflare Web Analytics** (privacy-friendly, no cookie, GDPR compliant)
- Form contatti: **Formspree**
- Donazioni: **PayPal JS SDK** (client-side, no backend) + bonifico bancario
- Mappa: **Google Maps embed** (caricata solo dopo consenso cookie)

## Struttura del progetto

```
site/
├── index.html        Pagina principale (SEO, Open Graph, Schema.org)
├── privacy.html      Informativa privacy (GDPR)
├── sitemap.xml       Sitemap (2 URL)
├── robots.txt        Direttive crawler + riferimento sitemap
├── CNAME             Dominio personalizzato (laboratoriotecnico.eu)
├── fonts/            Font Nunito (Regular, SemiBold, Bold, ExtraBold, Black)
├── images/           Hero, favicon, apple-touch-icon, logo
└── CLAUDE.md         Documentazione tecnica dettagliata e convenzioni
```

## Sviluppo locale

Nessun build necessario. Apri `index.html` direttamente nel browser, oppure
servi la cartella con un server statico per testare percorsi e form:

```bash
# Python
python -m http.server 8000

# oppure Node
npx serve .
```

Poi visita `http://localhost:8000`.

## Deploy

Il sito è pubblicato automaticamente da **GitHub Pages**: ogni push su `main`
aggiorna `https://laboratoriotecnico.eu`. Il dominio personalizzato è gestito dal
file `CNAME` e dai record DNS su Aruba (record A/AAAA GitHub + CNAME `www`).

> **Dopo ogni modifica** aggiorna il `<lastmod>` in `sitemap.xml` alla data odierna
> (`YYYY-MM-DD`) per le pagine modificate.

## Convenzioni

Le convenzioni di codice, stile e architettura sono documentate in dettaglio in
[`CLAUDE.md`](./CLAUDE.md). In sintesi:

- **Nessuno stile inline** (`style="..."`) né handler inline che mutano lo stile:
  tutto in classi nell'unico `<style>` di ciascuna pagina; classi condivise tra
  pagine usano lo stesso nome e la stessa regola
- Visibilità di banner/feedback gestita via classe `.hidden` + JS
- Responsive con media query a 900px, smooth scroll, angoli arrotondati
- Cookie/terze parti (PayPal, Google Maps) caricati solo previo consenso esplicito

## Contatti associazione

- **Denominazione:** Associazione Educativa Laboratorio Tecnico ODV
- **Sede legale:** Via Filippo Marchetti 1, 60125 Ancona (AN)
- **Codice Fiscale:** 93026570429
- **Telefono / WhatsApp:** 349 652 6946
- **Email:** info@laboratoriotecnico.eu · **PEC:** info@pec.laboratoriotecnico.eu
- **RUNTS:** Sez. Organizzazioni di Volontariato · Rep. n. 80820 · iscrizione 21/11/2022
- Ente del Terzo Settore — D.Lgs. 117/2017
