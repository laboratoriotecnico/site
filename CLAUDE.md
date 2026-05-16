# Laboratorio Tecnico ODV — Sito Web

## Contesto progetto
Sito statico istituzionale dell'Associazione Educativa Laboratorio Tecnico ODV di Ancona.
Ospitato su **GitHub Pages** (account: `laboratoriotecnico`) e raggiungibile su **laboratoriotecnico.eu**.

## Stack
- HTML/CSS/JS puro, nessun framework, nessuna dipendenza npm
- Font: **Nunito** via Google Fonts
- Hosting: GitHub Pages (branch `main`, root `/`)
- DNS: Aruba (4 record A GitHub + CNAME www)

## File del progetto
- `index.html` — pagina principale
- `privacy.html` — informativa privacy (GDPR)
- `bambini.png` — illustrazione hero (due bambini che giocano)
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
- Solo cookie tecnici + Google Fonts (trasferimento IP a Google LLC, base SCC)
- Nessun Analytics, nessun pixel pubblicitario
- Privacy policy su `privacy.html`

## Struttura sezioni (index.html)
1. Nav (sticky)
2. Hero (gradient blu, immagine bambini, badge ODV/1985)
3. Chi siamo (griglia testo + scheda anagrafica)
4. Attività (3 card)
5. 5×1000 (box scuro con CF copiabile)
6. Dona (card con importi + PayPal.me + info fiscali)
7. Contatti (indirizzo, tel/WA, email, PEC)
8. Footer (copyright 1985–2026 + iscrizione RUNTS completa)

## Note di stile
- Font: Nunito, arrotondato, sans-serif
- Angoli arrotondati ovunque (border-radius 24–40px)
- Onde SVG tra le sezioni
- Pulsante "Dona ora" sticky in basso a destra (sempre visibile)
- Nessun header/footer nelle pagine, nessun framework CSS