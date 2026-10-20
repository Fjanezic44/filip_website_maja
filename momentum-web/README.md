# Momentum – spletna stran

Statična spletna stran masažnega / fizioterapevtskega studia Momentum, izvožena iz Claude Designa.
Gostovanje: **Cloudflare Workers (static assets)**, samodejna objava ob vsakem `git push` na `main`.

## Struktura

| Pot | Namen |
| --- | --- |
| `public/index.html` | Spletna stran (ena datoteka, odzivna) |
| `public/404.html` | Stran za neobstoječe naslove |
| `public/favicon.png` | Ikona zavihka |
| `public/og-image.png` | Predogled pri deljenju (1200×630) |
| `public/robots.txt`, `public/sitemap.xml` | Za iskalnike |
| `public/_headers` | Varnostne glave in predpomnjenje |
| `wrangler.jsonc` | Nastavitve Cloudflare Workerja |

## Objava na Cloudflare (enkratno)

1. Cloudflare → **Workers & Pages** → **Create application** → **Import a repository** → poveži GitHub in izberi ta repo.
2. Ime projekta: `filip-website-maja` (mora biti enako kot `name` v `wrangler.jsonc`).
3. Build command: *(prazno)* · Deploy command: `npx wrangler deploy` · Root directory: `/`
4. **Save and Deploy** → stran je na `https://filip-website-maja.<racun>.workers.dev`.

## Ko je domena znana

1. V vseh datotekah zamenjaj `DOMENA.si` s pravo domeno (`index.html`, `robots.txt`, `sitemap.xml`).
2. Cloudflare → **Add a domain** → preveri, da so uvoženi MX/SPF/DKIM zapisi (e-pošta!) → pri registrarju zamenjaj nameserverje.
3. Worker → **Settings → Domains & Routes → Add → Custom domain**: `domena.si` in `www.domena.si`.
4. Preusmeritev www → glavna domena: **Rules → Redirect Rules → template "Redirect from WWW to root"**.
5. **SSL/TLS** → Full (strict), vključi **Always Use HTTPS**.

## Odprto

- Obrazec za rezervacijo samo prikaže potrditev – treba ga je povezati (Formspree / Web3Forms / Worker + e-pošta).
- Kontaktni podatki, urnik, storitve in cene so še začasni.

## Urejanje

`index.html` je zgrajena datoteka. Spremembe naredi v Claude Designu, ponovno izvozi, zamenjaj `public/index.html` in `git push`.
