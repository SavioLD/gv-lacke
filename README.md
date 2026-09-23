# GV-Lacke – Karriere / Ad-Funnel

Karriere-Landingpage für die **Grönenbacher Lackfabrik Gropper + Viandt GmbH (GV-Lacke)**,
Bad Grönenbach. Aufbau 1:1 an der ALWA-Karriereseite orientiert, umgesetzt im GV-Lacke-CI
und mit den unternehmenseigenen Positionen.

**Live-URL (nach Aktivierung von GitHub Pages):** https://saviold.github.io/gv-lacke/

## Struktur
- `index.html` – komplette Seite (HTML, CSS und JS inline, keine Build-Tools nötig)
- `bilder/` – Logo, Logo-Kurzform (mobil) und Fotos
- `.nojekyll`, `robots.txt`, `sitemap.xml`, `favicon.png`

## Corporate Identity
- **Rot:** `#E30613` (Logo, Buttons/CTAs, Akzente, Fortschrittsbalken)
- **Blau:** `#004883` (Überschriften, Icons, dunkle Sektionen/Hero/Footer)
- **Schrift:** Inter (Google Fonts)
- Logo aus dem übermittelten Logo-Bild abgeleitet (Voll- und Kurzform).

## Offene Stellen (ausschließlich diese kommuniziert)
Alle unbefristet, Vollzeit, sofortiger Eintritt – Standort Bad Grönenbach, Bezahlung nach Chemie-Tarif.
1. **Produktion Dosieranlage (m/w/d)**
2. **Abfüllerei (m/w/d)**
3. **Fachlagerist (m/w/d)** – Voraussetzung: Staplerschein & Führerschein Klasse B

(Inhalte aus den übermittelten Stellenbeschreibungen abgeleitet.)

## Vorfilter-Formular (eine Frage pro Schritt) – stellenabhängig
Reihenfolge: Stelle → Fragen → Kontaktdaten. Produktion/Abfüllerei = 6 Schritte, Fachlagerist = 7 Schritte
(die stellenspezifische Führerschein-Frage wird nur für den Fachlageristen eingeblendet).

| Frage | Kategorie | Logik |
|---|---|---|
| Deutschkenntnisse (Sicherheits-/Arbeitsanweisungen) | **Pflicht (K.-o.)** – alle | „Kaum / gar nicht“ → Bewerbung endet sofort |
| Bereitschaft zu körperlicher Tätigkeit (Produktion/Lager) | **Pflicht (K.-o.)** – alle | „Nein, eher nicht“ → Bewerbung endet sofort |
| Führerschein Klasse B | **Pflicht (K.-o.)** – nur Fachlagerist | nur eingeblendet für Fachlagerist; „Nein“ → Bewerbung endet sofort |
| Staplerschein | **Pflicht (K.-o.)** für Fachlagerist / **optional** sonst | Fachlagerist „Nein“ → Ende; Produktion „Nein“ → weiter, markiert |
| Erfahrung (Produktion/Lager) | optional | „Quereinsteiger:in“ → wird als „nicht erfüllt“ übertragen |

- **K.-o.:** freundlicher Abschlusshinweis + Verweis auf die übrigen offenen Stellen. **Wird NICHT an den Webhook gesendet.**
- **Optional nicht erfüllt:** Bewerber kommt normal weiter; Antwort wird übertragen und als „nicht erfüllt“ markiert (Feld `optionale_kriterien` + Suffix „— nicht erfüllt“).
- Nur berufsbezogene Kriterien (AGG-konform: keine Fragen zu Alter, Herkunft, Gesundheit, Religion, Familienstand).

## Mobile Laufruhe
Beim Fragenwechsel wird bewusst **nicht** gescrollt/fokussiert/neugeladen:
- kein `window.scrollTo`, kein `scrollIntoView`, kein `focus()`, kein Reload, kein Hash-Sprung beim Schrittwechsel.
- Formularcontainer mit fester Mindesthöhe (`min-height`) → Inhalt springt beim Wechsel nicht.
- Fortschrittsanzeige oben und Weiter-Button unten bleiben an fester Position.
- (Der einmalige Scroll zum Formular beim Klick auf „Jetzt bewerben“ in einer Stellen-Kachel ist eine bewusste Nutzeraktion, kein Fragenwechsel.)

## Webhook (LeadTable)
In `index.html` → `WEBHOOK_URL`. Es werden **nur abgeschlossene, qualifizierte** Bewerbungen als JSON gesendet.
Gesendete Felder u. a.: `vorname, nachname, email, telefon, stelle, deutsch, koerperliche_taetigkeit,
fuehrerschein_klasse_b, staplerschein, erfahrung, optionale_kriterien, starttermin, datum, lebenslauf, datenschutz, quelle, seite`.

## Optionaler Lebenslauf-Upload
Standardmäßig deaktiviert (`STORAGE_ENABLED = false`) – das Upload-Feld wird ausgeblendet, das Formular
funktioniert vollständig ohne Datei. Zum Aktivieren in `index.html`: `STORAGE_ENABLED = true` setzen und
`SUPABASE_URL` / `SUPABASE_KEY` / Bucket eintragen.

## Deployment
GitHub Pages: Repo-Einstellungen → Pages → Branch `main`, Ordner `/root`.
Danach live unter https://saviold.github.io/gv-lacke/

## Noch zu bestätigen / anzupassen (Platzhalter)
- **Kontakt-E-Mail:** `schneider@gv-lacke.de` (aus der Fachlagerist-Ausschreibung übernommen).
  **Impressum-/Datenschutz-Links** verweisen aktuell auf die Unternehmensseite – bei Bedarf durch die echten URLs ersetzen.
- Benefits: die von GV-Lacke gelieferten Leistungen sind eingebaut (13. Gehalt, 1.200 € Urlaubsgeld,
  37,5-Stunden-Woche, 50-€-Gutschein, Fahrtkostenzuschuss, Jahresprämie, Jubiläumsbonus,
  betriebl. Pflegeversicherung, Chemie-Tarif).
  Bitte kurz bestätigen: Ist der 50-€-Gutschein **monatlich** (aktuell so kommuniziert)?
- Weiteres/finales Bildmaterial für Hero und Sektionen kann jederzeit in `bilder/` ergänzt werden.

---
Karriereseite von Ländle Digital.
