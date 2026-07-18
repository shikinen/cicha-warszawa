# Cicha Warszawa — landing page

Statyczna strona (HTML + CSS, bez frameworka) inicjatywy mieszkańców Warszawy przygotowujących pozew przeciwko miastu w związku z nocnym hałasem. Mobile-first — główny ruch z kodu QR na ulotce.

## Pliki

- `index.html` — cała treść strony + mały skrypt obsługi formularza (AJAX → Formspree)
- `style.css` — style (design tokens w `:root`)

## Przed startem — do podmiany

1. **Formularz (Formspree):** załóż formularz na [formspree.io](https://formspree.io), skopiuj ID i podmień `YOUR_FORM_ID` w `index.html` (atrybut `action` formularza).
2. **E-mail kontaktowy** w stopce (`kontakt@cisza-warszawa.pl` to placeholder).
3. **URL poradnika** w sekcji „Zacznij zbierać dowody" (`instytut.ngo/dziennik-zdarzen-halasu`).

## Hosting

Strona jest czysto statyczna — działa wszędzie bez builda:

- **GitHub Pages** — włączone w tym repo (deploy z gałęzi `main`, katalog `/`).
- **Render** — New → Static Site → wskaż to repo; Build Command: puste, Publish Directory: `.`
- **Netlify / Cloudflare Pages** — analogicznie: repo → deploy, bez komendy builda.

## Dostępność / wydajność

- Animacja fali dźwiękowej wyłącza się przy `prefers-reduced-motion: reduce`.
- Walidacja formularza natywna (HTML `required`); po wysłaniu formularz zamienia się w podziękowanie bez przeładowania strony.
- Jedyna zależność zewnętrzna: Google Fonts (IBM Plex Sans / Mono).