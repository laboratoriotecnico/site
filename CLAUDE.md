# Laboratorio Tecnico ODV — Sito Web

## Contesto progetto
Sito statico istituzionale dell'Associazione Educativa Laboratorio Tecnico ODV di Ancona.
Ospitato su **GitHub Pages** (account: `laboratoriotecnico`) e raggiungibile su **laboratoriotecnico.eu**.

## Stack
- HTML/CSS/JS puro, nessun framework, nessuna dipendenza npm
- Font: **Nunito** caricati localmente da `/fonts/` (5 varianti: Regular, SemiBold, Bold, ExtraBold, Black)
- Hosting: GitHub Pages (branch `main`, root `/`)
- DNS: Aruba (4 record A + 4 AAAA GitHub + CNAME www)
- Analytics: **Plausible** (privacy-friendly, no cookies, GDPR compliant)
- Form contatti: **Formspree** (`action="https://formspree.io/f/FORM_ID"`)
- Mappa: **Google Maps embed** (coordinate: Via Filippo Marchetti 1, Ancona)

## File del progetto
- `index.html` — pagina principale (con SEO, OG tags, Schema.org)
- `privacy.html` — informativa privacy (GDPR)
- `bambini.png` — illustrazione hero (due bambini che giocano)
- `/fonts/` — directory con font Nunito (5 varianti TTF)
- `CNAME` — dominio personalizzato (`laboratoriotecnico.eu`)
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
- **CNAME** `www` → `laboratoriotecnico.github.io`
- Record MX, TXT, CNAME mail (admin, autoconfig, ftp, imap) lasciati invariati


- Link: `https://www.paypal.com/paypalme/LabTecnico/{importo}`
- Importi preset: €10, €25, €50, €100 + importo libero
- Benefici fiscali ODV: detrazione IRPEF 35% (fino a €30.000) oppure deduzione 10% reddito (max €70.000) — art. 83 D.Lgs. 117/2017

## 5×1000
- Sezione dedicata con copia CF negli appunti
- Dicitura corretta: "Sostegno degli enti del Terzo Settore iscritti nel RUNTS"

## Cookie / Privacy
- Cookie banner con accettazione in localStorage (`cookie_consent`)
- Solo cookie tecnici + trasferimento IP a Plausible (analytics GDPR compliant)
- **Nessun cookie di profilazione, nessun pixel pubblicitario**
- Privacy policy su `privacy.html`
- Honeypot nel form contatti per antispam

## Struttura sezioni (index.html)
1. **Nav** (sticky, logo + link anchor)
2. **Hero** (gradient blu, immagine bambini, badge ODV/1985, CTA buttons)
3. **Chi siamo** (griglia testo + scheda anagrafica con RUNTS/CF)
4. **Attività** (3 card: educazione minori, sostegno disabilità, volontariato)
5. **5×1000** (box scuro con CF copiabile)
6. **Dona** (card con importi preset + input custom + PayPal.me + info fiscali)
7. **Contatti** (griglia con lista contatti + mappa Google Maps + form contatti)
8. **Footer** (logo, copyright 1985–2026 + iscrizione RUNTS, link Privacy Policy)

## SEO e Meta tag
- **Open Graph** (og:type, og:url, og:title, og:description, og:image, og:locale, og:site_name)
- **Twitter Card** (twitter:card, twitter:title, twitter:description, twitter:image)
- **Structured Data** (JSON-LD Schema.org type: NGO, con contactPoint, address, areaServed)
- **Canonical URL** (`https://laboratoriotecnico.eu/`)
- **Meta keywords** (volontariato Ancona, ODV Marche, educazione minori, disabilità)

## Form di contatto
- Elemento `#contact-form` con Formspree
- Campi: nome*, email*, telefono (opz.)
- Honeypot antispam: `_gotcha` (nascosto)
- Redirect post-invio: `/?grazie=1`
- Validazione HTML5 (required, type="email")

## Note di stile
- Font: Nunito, arrotondato, sans-serif
- Angoli arrotondati ovunque (border-radius 24–40px)
- Onde SVG tra le sezioni (wave pattern)
- Pulsante "Dona ora" sticky in basso a destra (sempre visibile, z-index 999)
- Nessun framework CSS, responsive con media query a 900px
- Smooth scroll behavior (`scroll-behavior: smooth`)

## Donazioni
- Link: `https://www.paypal.com/paypalme/LabTecnico/{importo}`
- Importi preset: €10, €25, €50, €100 + input custom (€1–€9999)
- JavaScript: `selectAmount()`, `setCustomAmount()` per aggiornare URL PayPal
- Benefici fiscali ODV: detrazione IRPEF 35% (fino a €30.000) oppure deduzione 10% reddito (max €70.000) — art. 83 D.Lgs. 117/2017

## Mappa
- Embed Google Maps con coordinate: **43.6089572, 13.5033201**
- Zoom level: 13
- Responsive: 100% width, height 280px (contact grid), 300px (full screen)
- Border: 2px solid var(--sky-mid), border-radius var(--r-lg)