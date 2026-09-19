# AlcoCoding — site (źródło prawdy)

Statyczny szablon pod GitHub Pages (tryb legacy, `main /` — wystarczy push plików HTML).

## Struktura

```text
site/
├── index.html        # lista wpisów (render z posts/posts.json)
├── post.html         # szablon nowego wpisu (do kopiowania)
├── privacy.html      # polityka prywatności (RODO, zero trackerów)
├── o-mnie.html
├── style.css
├── feed.xml          # RSS — w przyszłości trigger do publikacji na FB
└── posts/
    ├── posts.json    # indeks wpisów (tytuł, data, excerpt, url, md, fb_status)
    ├── _szablon.md   # kanoniczny format wpisu w Markdown
    ├── *.md          # ŹRÓDŁO PRAWDY — te pliki idą potem na Facebooka
    └── *.html        # wersje do czytania (kanoniczny adres URL)
```

## Workflow: GitHub → Facebook (docelowo)

1. Piszesz wpis w `.md` (kopiujesz `_szablon.md`).
2. Kopiujesz `post.html` → `posts/RRRR-MM-DD-slug.html`, wklejasz treść.
3. Dopisujesz wpis do `posts.json` z `fb_status: draft` + dopisujesz item do `feed.xml`.
4. Push na `main` → strona żyje na https://alcocodingai.github.io/
5. Publikujesz ręcznie (na razie) ten sam tekst na https://www.facebook.com/AlcoCoding, potem ustawiasz `fb_status: posted` + doklejasz link.
6. W przyszłości: akcja bierze nowe `.md` z `main` i sama wysyła na FB (Graph API) — strona zostaje źródłem prawdy.

## Publikacja na GitHub Pages

```powershell
# z katalogu site/ — nadpisuje main w AlcoCodingAI.github.io
gh repo clone AlcoCodingAI/AlcoCodingAI.github.io deploy-tmp
Copy-Item site/* deploy-tmp/ -Recurse -Force
# + commit + push
```

Uwaga: Facebooka nie da się scrapować bez logowania (400 na fetch), więc 3 przykładowe wpisy odtworzyłem z Twojego korpusu autora (OCR, Reset Limitu, Emoji). Wklej mi 2-3 prawdziwe posty z FB, to podmienię treść 1:1.
