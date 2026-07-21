# Cicha Warszawa — landing page

Statyczna strona (HTML + CSS, bez frameworka) inicjatywy mieszkańców Warszawy przygotowujących pozew przeciwko miastu w związku z nocnym hałasem. Mobile-first — główny ruch z kodu QR na ulotce.

## Pliki

- `index.html` — cała treść strony + mały skrypt obsługi formularza (AJAX → Netlify Forms)
- `style.css` — style (design tokens w `:root`)
- `mjn_small_logo.png` — logo Miasto Jest Nasze

## Formularz — Netlify Forms

Formularz `name="zgloszenie"` używa wbudowanych Netlify Forms (darmowy limit: 100 zgłoszeń/mies.; spam wykryty przez Akismet nie wlicza się do limitu):

- `data-netlify="true"` + ukryte pole `form-name` — wymagane przez Netlify.
- **Honeypot** (`netlify-honeypot="bot-field"`) — ukryte pole; zgłoszenia z wypełnionym polem Netlify po cichu odrzuca.
- Wysyłka AJAX-em (POST `/` jako `application/x-www-form-urlencoded`), po sukcesie formularz zamienia się w podziękowanie.
- **localStorage** (`cw-zgloszenie-wyslane`) — po wysłaniu strona przy kolejnej wizycie od razu pokazuje podziękowanie (ochrona przed przypadkowym ponownym wysłaniem; czysto UX-owa).

Po wdrożeniu: w panelu Netlify → **Forms → Notifications** ustaw powiadomienie e-mail na adres kontaktowy. Gdyby spam przechodził — włącz reCAPTCHA w ustawieniach Forms.

## Hosting / deploy

1. Netlify → **Add new site → Import from Git** → wskaż to repo. Build command: puste, Publish directory: `.` (root).
2. Dodaj domenę własną w Netlify (Site → Domain management).
3. W Cloudflare DNS dodaj rekord CNAME wskazujący na `<site>.netlify.app` — **z włączonym proxy (pomarańczowa chmurka)**, żeby dostać darmową ochronę DDoS i cache przed Netlify.
4. E-mail: Cloudflare **Email Routing** → przekierowanie `kontakt@…` na prywatny Gmail; w Gmailu „Send mail as" przez `smtp.gmail.com` (hasło aplikacji).

## Przed startem — do podmiany

1. **E-mail kontaktowy** w stopce (`kontakt@cisza-warszawa.pl` to placeholder — podmień na adres w kupionej domenie).
2. **URL poradnika** w sekcji „Zacznij zbierać dowody" (`instytut.ngo/dziennik-zdarzen-halasu`).

## Dostępność / wydajność

- Animacja fali dźwiękowej wyłącza się przy `prefers-reduced-motion: reduce`.
- Walidacja formularza natywna (HTML `required`); po wysłaniu formularz zamienia się w podziękowanie bez przeładowania strony.
- Jedyna zależność zewnętrzna: Google Fonts (IBM Plex Sans / Mono).
