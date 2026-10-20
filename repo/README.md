# Momentum – spletna stran

Statična spletna stran fizioterapevtskega studia. Celotna stran je v eni datoteki `index.html` (brez zunanjih odvisnosti, brez build koraka).

## Struktura

| Datoteka | Namen |
| --- | --- |
| `index.html` | Spletna stran (namizje + telefon, odzivna) |
| `404.html` | Stran za neobstoječe naslove |
| `favicon.png` | Ikona zavihka |
| `robots.txt`, `sitemap.xml` | Za iskalnike |
| `_headers` | Varnostne glave in predpomnjenje (Cloudflare Pages) |
| `_redirects` | Preusmeritev www → glavna domena |
| `wrangler.toml` | Nastavitve za Cloudflare Pages (neobvezno) |

## 1. Objava na GitHub

```bash
cd filip_website_maja
# skopirajte vse datoteke iz te mape v repozitorij
git add .
git commit -m "Prva objava spletne strani"
git push origin main
```

## 2. Cloudflare Pages

1. Cloudflare → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
2. Izberite repozitorij `Fjanezic44/filip_website_maja`, veja `main`.
3. Nastavitve gradnje:
   - Framework preset: **None**
   - Build command: *(prazno)*
   - Build output directory: `/`
4. **Save and Deploy**. Stran bo dostopna na `filip-website-maja.pages.dev`.

Vsak `git push` na `main` stran samodejno posodobi.

## 3. Povezava domene

1. Domeno dodajte v Cloudflare (**Add a site**) in pri registrarju domene zamenjajte imenske strežnike (nameservers) na tista, ki jih pokaže Cloudflare.
2. V projektu Pages → **Custom domains** → **Set up a custom domain** → vpišite `DOMENA.si`, nato še `www.DOMENA.si`.
3. Cloudflare samodejno ustvari DNS zapise (CNAME) in SSL certifikat.
4. **SSL/TLS** → način **Full (strict)**, vključite **Always Use HTTPS**.

## 4. Pred objavo zamenjajte

- `DOMENA.si` v datotekah `index.html`, `robots.txt`, `sitemap.xml`, `_redirects` z vašo pravo domeno.
- Dodajte `og-image.png` (1200×630) za predogled pri deljenju na družbenih omrežjih.
- Kontaktni podatki, urnik, storitve in cene so še začasni.
- Obrazec za rezervacijo trenutno samo prikaže potrditev – za pravo pošiljanje ga je treba povezati (npr. Cloudflare Worker + e-pošta, Formspree ali sistem za rezervacije).

## Urejanje

`index.html` je zgrajena (bundled) datoteka. Spremembe naredite v izvornem dizajnu in stran ponovno izvozite, nato zamenjajte `index.html` in naredite `git push`.
