# Associazione Educativa Laboratorio Tecnico ODV — Sito Web

## Istruzioni per Claude
- **CLAUDE.md deve essere sempre aggiornato.** Dopo ogni modifica al progetto (struttura file, stack, comportamenti, convenzioni), aggiorna immediatamente le sezioni pertinenti di questo file.
- **README.md deve essere sempre aggiornato.** Dopo ogni modifica al progetto (struttura file, stack, sviluppo locale, deploy, convenzioni), aggiorna immediatamente le sezioni pertinenti di `README.md`.

## Contesto progetto
Sito statico istituzionale dell'Associazione Educativa Laboratorio Tecnico ODV di Ancona.
Ospitato su **GitHub Pages** (account: `laboratorio-tecnico`) e raggiungibile su **laboratoriotecnico.eu**.

## Stack
- HTML/CSS/JS puro, nessun framework, nessuna dipendenza npm
- **Tutto in `index.html`**: CSS nell'unico `<style>` in `<head>`, JS nell'unico `<script>` prima di `</body>`. Lo styling dei singoli elementi è prevalentemente **inline** (`style="..."`); le classi CSS coprono solo i pattern ripetuti. Nessun file `.css`/`.js` esterno — modifiche a stile/script vanno fatte dentro `index.html`
- Font: **Nunito** caricati localmente da `/fonts/` (5 varianti: Regular, SemiBold, Bold, ExtraBold, Black)
- Hosting: GitHub Pages (branch `main`, root `/`)
- DNS: Aruba (4 record A + 4 AAAA GitHub + CNAME www)
- Analytics: **Cloudflare Web Analytics** (privacy-friendly, no cookies, GDPR compliant, gratuito)
- Form contatti: **Formspree** (`action="https://formspree.io/f/xkoewwpg"`)
- Mappa: **Google Maps embed** (coordinate: Via Filippo Marchetti 1, Ancona)

## File del progetto
- `index.html` — pagina principale (con SEO, OG tags, Schema.org)
- `privacy.html` — informativa privacy (GDPR)
- `/images/` — directory con tutte le immagini e icone:
  - `bambini.png` — illustrazione hero (due bambini che giocano)
  - `favicon.svg` — icona SVG con sfondo bianco (per browser)
  - `apple-touch-icon.png` — icona PNG 180×180 (per iOS)
  - `logo.svg` — logo orizzontale (usato nel nav)
- `/fonts/` — directory con font Nunito (5 varianti TTF)
- `sitemap.xml` — sitemap (2 URL: `/` priority 1.0, `/privacy.html` priority 0.3). **Aggiorna SEMPRE il `<lastmod>` alla data odierna per ogni pagina modificata** (formato `YYYY-MM-DD`) a ogni modifica del progetto
- `CNAME` — dominio personalizzato (`laboratoriotecnico.eu`)
- `robots.txt` — direttive crawler (`Allow: /`) + riferimento alla sitemap
- `README.md` — documentazione introduttiva del progetto (overview, stack, struttura, sviluppo locale, deploy, convenzioni)
- `.gitignore` — esclude `.idea/` e file IntelliJ

## Identità associazione
- **Denominazione completa:** Associazione Educativa Laboratorio Tecnico ODV
- **Natura giuridica:** Organizzazione di Volontariato (ODV)
- **Codice Fiscale:** 93026570429
- **Sede legale:** Via Filippo Marchetti 1, 60125 Ancona (AN)
- **Fondazione:** 1° settembre 1985
- **Telefono / WhatsApp:** 349 652 6946
- **Email:** info@laboratoriotecnico.eu
- **PEC:** info@pec.laboratoriotecnico.eu
- **Sito:** laboratoriotecnico.eu
- **RUNTS:** Sez. Organizzazioni di Volontariato · Rep. n. 80820 · iscrizione 21/11/2022 · DDS Regione Marche n. 399/2022
- **Normativa:** D.Lgs. 117/2017 – Codice del Terzo Settore

## Attività
- Attività educative per minori
- Sostegno alle persone con disabilità
- Volontariato e cittadinanza attiva

## Palette colori
```
--sky:      #5BB8F5
--sky-lt:   #EAF5FD
--sky-mid:  #B8DEFA
--blue:     #1A6BBF
--blue-dk:  #0D4A8A
--red:      #E63946
--red-dk:   #C1121F
--sun:      #FFD166
--dark:     #111827
--muted:    #4B5563
--paypal:   #0070BA
```

## DNS (Aruba)
- 4 record **A** `@` → IP GitHub Pages (185.199.108-111.153)
- 4 record **AAAA** `@` → IP GitHub Pages IPv6 (2606:50c0:8000-8003::153)
- **CNAME** `www` → `laboratorio-tecnico.github.io`
- Record MX, TXT, CNAME mail (admin, autoconfig, ftp, imap) lasciati invariati


- Integrazione PayPal JS SDK (client-side) — vedi sezione Donazioni
- Importi preset: €10, €25, €50, €100 + importo libero
- Benefici fiscali ODV: detrazione IRPEF 35% (fino a €30.000) oppure deduzione 10% reddito (max €70.000) — art. 83 D.Lgs. 117/2017

## 5×1000
- Sezione dedicata con copia CF negli appunti
- Dicitura corretta: "Sostegno degli enti del Terzo Settore iscritti nel RUNTS"

## Cookie / Privacy
- **Banner consenso cookie** — `#cookie-banner` (fixed bottom), preferenza salvata in `localStorage` (`cookie_consent`: `'accepted'` | `'rejected'`)
- **Cloudflare Web Analytics** — nessun cookie, caricato sempre senza consenso
- **PayPal JS SDK** — caricato dinamicamente solo se `cookie_consent === 'accepted'`; prima del consenso mostra `#paypal-no-consent` con pulsante "Accetta cookie" → chiama `cookieChoice('accepted')` direttamente
- **Google Maps** — iframe iniettato dinamicamente solo se `cookie_consent === 'accepted'`; prima del consenso mostra `#map-placeholder` con solo pulsante "Accetta cookie" → chiama `cookieChoice('accepted')` direttamente
- **Nessun cookie di profilazione, nessun pixel pubblicitario**
- `loadThirdParty()` carica PayPal SDK + mappa; `initPayPal()` inizializza i pulsanti PayPal (chiamata da `script.onload`)
- Privacy policy su `privacy.html`
- Honeypot nel form contatti per antispam

## Struttura sezioni (index.html)
1. **Nav** (sticky, logo + link anchor)
2. **Hero** (gradient blu, immagine bambini, badge ODV/1985, CTA buttons)
3. **Chi siamo** (griglia testo + scheda anagrafica con RUNTS/CF)
4. **Attività** (3 card: educazione minori, sostegno disabilità, volontariato)
5. **5×1000** (box scuro con CF copiabile)
6. **Dona** (card con importi preset + input custom + PayPal JS SDK buttons + info fiscali)
7. **Contatti** (griglia con lista contatti + mappa Google Maps + form contatti)
8. **Footer** (copyright 1985–2026 + iscrizione RUNTS, link Privacy Policy)

## SEO e Meta tag
- **Open Graph** (og:type, og:url, og:title, og:description, og:image, og:locale, og:site_name)
- **Twitter Card** (twitter:card, twitter:title, twitter:description, twitter:image)
- **Structured Data** (JSON-LD Schema.org type: NGO, con contactPoint, address, areaServed)
- **Canonical URL** (`https://laboratoriotecnico.eu/`)
- **Meta keywords** (volontariato Ancona, ODV Marche, educazione minori, disabilità)

## Form di contatto
- Elemento `#contact-form` con Formspree
- Campi: nome* (`#f-nome`), email* (`#f-email`), telefono (`#f-telefono`), oggetto (`#f-oggetto`), messaggio* (`#f-messaggio`)
- Tutti i `<label>` hanno `for` collegato all'`id` del campo
- Honeypot antispam: `_gotcha` con `aria-hidden="true"` e `aria-label="Non compilare"`
- Redirect post-invio: `/?grazie=1`
- Submit tramite `addEventListener('submit', ...)` — nessun `onsubmit` inline
- Logica invio: flag `ok = res.ok` nel try/catch, nessun `throw` locale

## Note di stile
- Font: `'Nunito', system-ui, sans-serif` — dichiarato esplicitamente su `body`, `input`, `select`, `textarea`, `button`; non più tramite `var(--font)` negli stili inline
- Angoli arrotondati ovunque (border-radius 24–40px)
- **Nessuno stile inline (vale per OGNI pagina: `index.html`, `privacy.html` e qualsiasi pagina futura)**: nessun file HTML deve contenere attributi `style="..."` né handler inline che mutano lo stile (`onfocus`/`onblur`/`onmouseover`/`onmouseout`). Tutto è in classi nell'unico `<style>` della pagina. Aggiungendo markup (o creando una nuova pagina), usa/crea classi — non reintrodurre `style="..."`. **Classi condivise tra pagine**: se uno stile serve in più pagine (es. `.nav-logo-img`, `.footer-copy-group`, `.footer-inner`, `.footer-copy`, `.mobile-br`/`.mobile-hide`) usa lo **stesso nome e la stessa regola** in ogni `<style>` — non inventare nomi divergenti per lo stesso scopo. Convenzioni `index.html`: utility (`.hidden`, `.col-full`, `.c-white`, `.c-dark`, `.link-blue`, `.mt-r08`); componenti (`.field` + `.field--select`/`.field--textarea` con `.field:focus`; `.btn-accept`, `.btn-submit` con `:hover`; `.dona-bonifico`/`.dona-fiscal`/`.dona-box-*`; `.pp-no-consent`, `.pp-fallback*`; `.map-wrap`/`.map-placeholder`/`.map-iframe`). Gli stati hover/focus che prima erano `onfocus/onblur/onmouseover/onmouseout` ora sono regole `:focus`/`:hover` — non ripristinarli inline
- **Visibilità via `.hidden` + JS**: elementi tipo `#cookie-banner`, `#paypal-no-consent`, `#form-feedback`, honeypot partono con classe `.hidden` (`display:none`). Il JS li mostra/nasconde impostando `element.style.display` inline (che vince su `.hidden`). **Non** aggiungere `display:flex` (o altro `display`) alla regola `#cookie-banner`: lo stato iniziale nascosto dipende dal fatto che l'id non imposti `display`, lasciando vincere `.hidden`
- **Onde SVG tra le sezioni (divisori)**: 5 `<svg class="wave ...">`. Lo sfondo (regione trasparente sopra la curva) combacia con la sezione **sopra** via classe: `.wave-white` (= white) o `.wave-sky` (= #EAF5FD); il `fill="<colore>"` dell'SVG combacia con la sezione **sotto**. **Eccezione**: l'onda della hero (subito dopo `.hero-inner`, dentro `#hero`) ha solo `class="wave"` (nessuna `.wave-*`) perché sopra la curva deve mostrare il gradiente blu del hero — non aggiungere uno sfondo. `.wave` ha `margin-bottom: -1px` per coprire la cucitura antialiasata di 1px (causata da `preserveAspectRatio="none"` con altezza frazionaria) — non rimuoverlo. Toccando un'onda, mantieni la coerenza colore con le sezioni adiacenti
- Pulsante "Dona ora" sticky in basso a destra (sempre visibile, z-index 999)
- Nessun framework CSS, responsive con media query a 900px
- Smooth scroll behavior (`scroll-behavior: smooth`)
- **Mobile footer**: testo copyright va a capo con `<br class="mobile-br">` e il separatore " · " si nasconde con `.mobile-hide`

## JavaScript
- **Funzioni globali** (richiamate da handler inline `onclick`/`oninput`/`onfocus` nell'HTML — devono restare nello scope globale, non incapsularle in moduli/IIFE): `cookieChoice`, `loadThirdParty`, `initPayPal`, `selectAmount`, `setCustomAmount`, `copyIBAN`, `copyCF`
- **Stato donazione**: `currentAmount` (var globale, default 25); letta in `createOrder` di `paypal.Buttons()`
- **Scroll-spy**: evidenzia il link nav della sezione corrente; itera su `section[id]`. `#hero` è un `<div>` (non `<section>`) quindi è **intenzionalmente escluso** — se lo converti in `<section>` aggiungi un `<a href="#hero">` o il primo link resterà evidenziato a inizio pagina. Handler throttlato con `requestAnimationFrame` + listener `{ passive: true }` — mantenere il throttle (`offsetTop` in loop a ogni evento scroll causa reflow forzato)
- **Form contatti**: l'`_subject` (`#contact-subject`) viene aggiornato dinamicamente dal campo nome via `addEventListener('input')`
- **clipboard**: `copyIBAN`/`copyCF` delegano all'helper `copyToClipboard(text, selector, okLabel, defaultLabel)`; su `.catch` (permesso negato) il pulsante mostra "⚠️ Copia manuale: <testo>" per 4s
- **Markup iniettato da JS usa classi**: `paypalFallback()` (`.pp-fallback`/`.pp-fallback-text`/`.pp-fallback-link`), messaggio di ringraziamento (`p.className = 'dona-thanks'`), iframe mappa (`class="map-iframe"`). Collasso mappa in `loadThirdParty()`: dopo aver iniettato l'iframe fa `mp.classList.remove('map-placeholder')` + `mp.style.height='100%'` (la classe `.map-placeholder` porta flex/padding/sfondo del placeholder; va rimossa, non basta sovrascrivere lo stile)

## Donazioni
- Integrazione: **PayPal JS SDK** (client-side, no backend)
- Client ID live: `AdYELd-9IBTRGEUpQAbPAsTmHeEB_SZlrtUNywuIXNGEMRc-6vdJfcn6yrzRRyzW05O4mM7xnTcV5WpC`
- SDK URL: `https://www.paypal.com/sdk/js?client-id=...&currency=EUR&locale=it_IT&intent=capture&enable-funding=card&disable-funding=credit,paylater`
- Mostra due pulsanti: PayPal + Carta di credito/debito (`enable-funding=card`)
- `paypal.Buttons()` usa `style: { label: 'donate' }` → con `locale=it_IT` il pulsante mostra "Dona" (non "Paga")
- Importi preset: €10, €25, €50, €100 + input custom (€1–€9999)
- JavaScript: `currentAmount` (var globale), `selectAmount()`, `setCustomAmount()` aggiornano `currentAmount`; `paypal.Buttons()` legge `currentAmount` in `createOrder`
- Campo CF donatore (`#donor-cf`, opzionale): incluso in `description` e `custom_id` dell'ordine PayPal
- Post-pagamento: notifica automatica via Formspree `https://formspree.io/f/xlgvrrbk` (campi: nome, email, importo, codice_fiscale, transaction_id) + messaggio di ringraziamento inline
- **Bonifico bancario** (alternativa a PayPal, box nella card Dona): Intesa Sanpaolo · Filiale Accentrata · Piazza Paolo Ferrari 10 — IBAN `IT51R0306909606100000013451` (intestato all'associazione, copiabile con `copyCF`/`copyIBAN`)
- **Fallback `paypalFallback()`**: se l'SDK PayPal non carica (`s.onerror`) o i pulsanti vanno in errore (`onError` di `paypal.Buttons()`), `#paypal-button-container` mostra un messaggio che rimanda al bonifico e a info@laboratoriotecnico.eu
- **Stacking / z-index**: `#paypal-button-container` ha `isolation: isolate` per confinare lo z-index dell'iframe PayPal inline (altrimenti durante lo scroll passa sopra la nav). Ordine z-index: `nav` 1000 < `#cookie-banner` 1001; `.sticky-dona` 999. Il modale di pagamento PayPal è montato su `document.body` (fuori dal container) e resta correttamente sopra tutto.
- Benefici fiscali ODV: detrazione IRPEF 35% (fino a €30.000) oppure deduzione 10% reddito (max €70.000) — art. 83 D.Lgs. 117/2017

## Mappa
- Embed Google Maps con coordinate: **43.6089572, 13.5033201**
- Zoom level: 13
- Responsive: 100% width, height 280px (contact grid), 300px (full screen)
- Border: 2px solid var(--sky-mid), border-radius var(--r-lg)