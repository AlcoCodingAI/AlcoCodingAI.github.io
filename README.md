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

1. Wypełnij lokalny formularz `C:\ac\nowy-wpis.html` (nie trafia na Pages).
2. Pobierz pakiet JSON do `C:\ac\site\inbox\` (obrazki wcześniej wrzuć do `C:\ac\site\images\`).
3. Uruchom `powershell -ExecutionPolicy Bypass -File C:\ac\nowy-wpis.ps1`.
4. Skrypt generuje `.md` + `.html`, aktualizuje `posts.json` / `feed.xml` / `index.html` i pyta o zgodę.
5. Po wpisaniu `T` idzie push na `main` → Pages publikuje automatycznie.
6. Wpisy z `fb_status: draft` czekają na ręczną publikację na FB; potem formularzowo oznaczasz `posted` + link.

## Publikacja na GitHub Pages

```powershell
# z katalogu site/ — nadpisuje main w AlcoCodingAI.github.io
gh repo clone AlcoCodingAI/AlcoCodingAI.github.io deploy-tmp
Copy-Item site/* deploy-tmp/ -Recurse -Force
# + commit + push
```

Uwaga: Facebooka nie da się scrapować bez logowania (400 na fetch), więc 3 przykładowe wpisy odtworzyłem z Twojego korpusu autora (OCR, Reset Limitu, Emoji). Wklej mi 2-3 prawdziwe posty z FB, to podmienię treść 1:1.
