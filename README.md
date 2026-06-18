# Pavelka 31 Kemp

Web brankářského kempu Jaroslava Pavelky — termíny, registrace s QR platbou (SPAYD), galerie, pravidla, merch a kontakt.

## Nasazení (deploy)

Stránka je statická, nepotřebuje build krok. Stačí servírovat `index.html`.

- **GitHub Pages** — pushni repo, v Settings → Pages nastav branch `main` / root. Web pojede na `https://<user>.github.io/<repo>/`.
- **Netlify / Vercel** — přetáhni složku nebo připoj repo, žádné build commandy, publish directory = root.
- **Vlastní hosting** — nahraj `index.html` na server.

`index.html` je self-contained (runtime, styly i úvodní foto jsou vložené uvnitř). **Složku `media/` nasazuj vždy spolu s `index.html`** — fotky a videa galerie se načítají z ní za běhu (záměrně nejsou vložené, ať HTML nenabobtná o megabajty videa). Online připojení je potřeba jen pro:
- Google Fonts (Bebas Neue, Inter, JetBrains Mono),
- generování QR kódu (api.qrserver.com).

## Vývoj / úpravy

Zdroj je **`Pavelka 31 Kemp.dc.html`** (+ `support.js` runtime). Po úpravách zdroje znovu vygeneruj `index.html` (rebundle).

## Než půjde web naostro — doplnit od klienta

Vyhledej v `Pavelka 31 Kemp.dc.html` značky `DOPLNIT` a `TODO`:

- **Platba** (nahoře v logice): `PAYMENT_IBAN`, `PAYMENT_BIC`, `PAYMENT_ACCOUNT_PRETTY`, částka a variabilní symbol.
- **Termíny** (`CAMPS`): reálné kempy, data, místa, ceny, kapacity.
- **Pravidla** (`RULES`): finální znění všech 6 sekcí.
- **O Jaroslavovi** (`CAREER` + texty): bio, kluby, citát.
- **Kontakt**: skutečný e-mail, telefon, IČO/adresa, embed Google Maps.
- **Galerie**: reálné fotky/videa už jsou ve složce `media/` (doplň další dle potřeby).
- Formuláře (registrace, kontakt, merch) jsou zatím jen frontend — napojit na backend / e-mail / platební bránu.
