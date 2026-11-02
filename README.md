# Sito web personale

Sito statico: `index.html` + `style.css`, niente framework e niente build.
Pubblicato gratis con **GitHub Pages**.

## Struttura

```
index.html   contenuti (testi, servizi, lavori, CV, contatti)
style.css    grafica (colori in cima al file, nella sezione :root)
cv.pdf       il CV scaricabile, generato da cv/cv.html
cv/cv.html   sorgente del CV (senza dati personali)
img/         immagini dei lavori (facoltativa)
```

## Modificare i contenuti

Apri `index.html` e sostituisci i testi segnaposto ("Nome Cognome", "Servizio uno", ecc.).
- **WhatsApp**: nel link `https://wa.me/390000000000` metti il numero con prefisso, senza `+` né spazi.
- **CV**: modifica `cv/cv.html`, poi rigenera il PDF con il comando qui sotto.
- **Colore principale**: cambia `--accent` in `style.css`.

Anteprima in locale:

```bash
python3 -m http.server 8765
```

poi apri http://localhost:8765

Rigenerare `cv.pdf` (serve Google Chrome):

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --no-pdf-header-footer --print-to-pdf="$PWD/cv.pdf" "file://$PWD/cv/cv.html"
```

## Pubblicare gratis su GitHub Pages

1. Crea un account su https://github.com (gratis).
2. Crea un repository pubblico chiamato **`<tuo-utente>.github.io`**.
3. Da questa cartella:
   ```bash
   git init
   git add .
   git commit -m "Primo sito"
   git branch -M main
   git remote add origin https://github.com/<tuo-utente>/<tuo-utente>.github.io.git
   git push -u origin main
   ```
4. Su GitHub: **Settings → Pages → Source: Deploy from a branch → `main` / `(root)`**.
5. Dopo un minuto il sito è online su `https://<tuo-utente>.github.io` (HTTPS incluso).

Ogni modifica successiva: `git add . && git commit -m "aggiornamento" && git push`.

## Dominio personalizzato (facoltativo)

L'indirizzo `<tuo-utente>.github.io` è gratuito per sempre. Un dominio tipo `nomecognome.it`
invece si paga (di solito pochi euro il primo anno, poi ~10–20 €/anno) — register.it non
offre domini gratuiti in modo stabile, solo promozioni sul primo anno.

Se lo registri, collegarlo a GitHub Pages è gratis:
1. Su GitHub: **Settings → Pages → Custom domain** → scrivi `www.nomecognome.it`.
2. Nel pannello DNS del registrar aggiungi:
   - `CNAME` `www` → `<tuo-utente>.github.io`
   - 4 record `A` per `@` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
3. Attendi la propagazione e spunta **Enforce HTTPS**.
