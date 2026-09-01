# Nettside — Tømrer Morten Rønningen AS

En enkel, statisk one-page nettside. Ingen byggeverktøy nødvendig — bare rene HTML/CSS-filer.

## Innhold i mappen
```
index.html                        selve siden
styles.css                        all styling
assets/logo.png                   original logo (kvadratisk, sort bakgrunn)
assets/logo-ink-crop.png          logo i mørk versjon, beskåret, transparent bakgrunn (brukes i header)
assets/logo-white-crop.png        logo i lys versjon, beskåret, transparent bakgrunn (brukes i footer)
```

## 1. Legg til egne prosjektbilder
I "Nylige prosjekter"-seksjonen ligger det fire fargede plassholdere (`project-tile--a` til `--d` i `styles.css`). Bytt dem ut med ekte bilder:

1. Legg bildene i `assets/`, f.eks. `assets/prosjekt-tilbygg-1.jpg`
2. I `index.html`, finn en `<figure class="project-tile ...">` og legg til bildet som bakgrunn, f.eks.:
   ```html
   <figure class="project-tile" style="background-image:url('assets/prosjekt-tilbygg-1.jpg')">
     <figcaption>Tilbygg<span>Sunde Bru</span></figcaption>
   </figure>
   ```
3. Du kan gjerne legge til flere `<figure>`-elementer enn de fire som er der nå — rutenettet tilpasser seg automatisk.

Bruk gjerne skjermbildene/bildene fra Facebook-siden her.

## 2. Publisere med GitHub + Cloudflare Pages

### A. Legg koden i et GitHub-repo
1. Opprett et nytt repo på [github.com/new](https://github.com/new), f.eks. `tomrer-ronningen-nettside`
2. Last opp disse filene (via "Add file → Upload files" i nettleseren, eller via git):
   ```
   git init
   git add .
   git commit -m "Første versjon av nettsiden"
   git branch -M main
   git remote add origin https://github.com/<ditt-brukernavn>/tomrer-ronningen-nettside.git
   git push -u origin main
   ```

### B. Koble til Cloudflare Pages
1. Logg inn på [dash.cloudflare.com](https://dash.cloudflare.com)
2. Gå til **Workers & Pages → Create → Pages → Connect to Git**
3. Velg repoet du nettopp opprettet
4. Under build-innstillinger:
   - **Build command:** la stå tom (ingen bygg nødvendig — det er ren HTML/CSS)
   - **Build output directory:** `/`
5. Trykk **Save and Deploy**

Cloudflare gir deg automatisk en `*.pages.dev`-adresse med gratis SSL. Hver gang du pusher endringer til `main` på GitHub, oppdateres siden automatisk.

### C. Koble på eget domene (valgfritt)
1. I Cloudflare Pages-prosjektet, gå til **Custom domains**
2. Legg til domenet (f.eks. `tomrerronningen.no`)
3. Hvis domenet allerede ligger hos Cloudflare, ordnes DNS automatisk. Hvis ikke, følg instruksjonene for å peke DNS-en dit.

## 3. Ting du bør fylle inn/avklare før lansering
- Bytt ut plassholder-prosjektbildene (se punkt 1)
- Legg til direkte lenke til Facebook-siden i kontaktseksjonen (`index.html`, søk etter "Facebook")
- Vurder om dere ønsker e-post/kontaktskjema i tillegg til telefon
- Sjekk at telefonnummeret og adressen er riktig format for `tel:`-lenken (`+4793882057`)
