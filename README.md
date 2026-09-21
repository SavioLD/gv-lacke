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
Beide unbefristet, Vollzeit, sofortiger Eintritt – Standort Bad Grönenbach.
1. **Produktion Dosieranlage (m/w/d)**
2. **Abfüllerei (m/w/d)**

(Inhalte aus den übermittelten Stellenbeschreibungen abgeleitet.)

## Vorfilter-Formular (eine Frage pro Schritt)
Reihenfolge: Stelle → 4 Fragen → Kontaktdaten (6 Schritte gesamt).

| Frage | Kategorie | Logik |
|---|---|---|
| Deutschkenntnisse (Sicherheits-/Arbeitsanweisungen) | **Pflicht (K.-o.)** | „Kaum / gar nicht“ → Bewerbung endet sofort |
| Bereitschaft zu körperlicher Produktionstätigkeit | **Pflicht (K.-o.)** | „Nein, das ist eher nichts für mich“ → Bewerbung endet sofort |
| Erfahrung in Produktion / mit Lacken, Farben, Chemie | optional | „Quereinsteiger:in“ → wird als „nicht erfüllt“ übertragen |
| Staplerschein | optional | „Nein“ → wird als „nicht erfüllt“ übertragen |

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
erfahrung, staplerschein, optionale_kriterien, starttermin, datum, lebenslauf, datenschutz, quelle, seite`.

## Optionaler Lebenslauf-Upload
Standardmäßig deaktiviert (`STORAGE_ENABLED = false`) – das Upload-Feld wird ausgeblendet, das Formular
funktioniert vollständig ohne Datei. Zum Aktivieren in `index.html`: `STORAGE_ENABLED = true` setzen und
`SUPABASE_URL` / `SUPABASE_KEY` / Bucket eintragen.

## Deployment
GitHub Pages: Repo-Einstellungen → Pages → Branch `main`, Ordner `/root`.
Danach live unter https://saviold.github.io/gv-lacke/

## Noch zu bestätigen / anzupassen (Platzhalter)
- **Kontakt-E-Mail** (`bewerbung@gv-lacke.de`) sowie **Impressum-/Datenschutz-Links** – bitte durch die
  echten Angaben von GV-Lacke ersetzen. Aktuell auf die Unternehmensseite verlinkt.
- Ggf. konkrete Benefits (z. B. Urlaubstage, Sonderzahlungen) ergänzen – aktuell bewusst allgemeine „Klassiker“.
- Weiteres/finales Bildmaterial für Hero und Sektionen kann jederzeit in `bilder/` ergänzt werden.

---
Karriereseite von Ländle Digital.
