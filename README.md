# Stein Advocaten — steinadvocatenzwolle.nl

Statische website (platte HTML/CSS, geen build-stap nodig). Klaar om te hosten op Cloudflare Pages via GitHub.

## Structuur

- `index.html`, `over.html`, `redactie.html`, `contact.html`, `privacybeleid.html`, `cookiebeleid.html`
- `rechtsgebieden/` — overzicht + 11 pagina's per rechtsgebied
- `nieuws/` — overzicht + 5 nieuwsartikelen
- `assets/css/style.css`, `assets/img/` — stijl en illustraties
- `.github/workflows/deploy.yml` — GitHub Actions workflow die bij elke push naar `main` automatisch naar Cloudflare Pages deployt

## Eenmalig instellen

1. **GitHub repo**: maak een lege repository aan (bijv. `stein-advocaten-zwolle`) en push deze map naar de `main`-branch.
2. **Cloudflare Pages project**: maak in het Cloudflare dashboard een Pages-project aan met de naam `stein-advocaten-zwolle` (moet overeenkomen met `projectName` in `.github/workflows/deploy.yml`).
3. **GitHub secrets**: voeg in de repo-instellingen (Settings → Secrets and variables → Actions) twee secrets toe:
   - `CLOUDFLARE_API_TOKEN` — een Cloudflare API-token met de rechten "Cloudflare Pages: Edit"
   - `CLOUDFLARE_ACCOUNT_ID` — het Cloudflare account-ID
4. **Custom domain**: koppel `steinadvocatenzwolle.nl` aan het Cloudflare Pages-project via het dashboard (Pages-project → Custom domains). Zorg dat de domeinnaam als zone in hetzelfde Cloudflare-account staat, of wijzig de nameservers naar Cloudflare.
5. Push naar `main` → de GitHub Action deployt automatisch.

## Analytics (optioneel)

De privacy- en cookiepagina's gaan uit van Cloudflare Web Analytics (cookieloos). Voeg dit toe via Cloudflare dashboard → Pages-project → Analytics → "Enable Web Analytics", dit voegt automatisch een script toe zonder dat de code hier hoeft te wijzigen.

## Google Search Console

1. Voeg het domein toe als property in Google Search Console (op het account waaronder de site geïndexeerd moet worden).
2. Verifieer eigendom via de DNS-TXT-record methode (aan te maken bij de DNS-instellingen van de zone in Cloudflare).
3. Dien na verificatie de sitemap in: `https://steinadvocatenzwolle.nl/sitemap.xml`.
4. Vraag via "URL-inspectie" indexering van de homepage aan.
