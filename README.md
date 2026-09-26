# BacPack

Past **BAC (Algerian baccalauréat) exam papers**, 2008–2025, used by the
**BACBIT** exam-prep app's "Past BAC topics" screen. Papers are downloaded on
demand over GitHub raw URLs and cached on device — nothing is bundled in the
APK.

## Layout

```
papers/
  maths/        YYYY-principal.pdf | 2017-rattrapage.pdf | 2017-remplacement.pdf
  physics/      (same session naming)
  electric/     (Electrical engineering / Technologie)
  english/
  histgeo/      (History & Geography)
  islamic/
  arabic/
  french/
  philosophy/
  tamazight/
```

- `principal` = Main session (June). Filenames are the API contract — don't
  rename without updating the app's papers manifest.
- Main session is complete for every subject; Replacement/Rattrapage sessions
  are included only where a copy exists (2016–2017).
- Most PDFs embed the official correction sections where the source document
  provided them.

## How the app uses this

The app builds its download list from the raw GitHub URL of this repo plus
`<subject>/<file>.pdf`. Adding a paper = drop the PDF in the subject folder
and push. New files with existing names need no app update.

## Status

**192 papers** across 10 subjects (2008–2025): the 6 science/language
subjects have 18 Main-session years each; Arabic, French, Philosophy and
Tamazight have 17–18 Main-session years each; 8 Replacement/Rattrapage papers
(2016–2017) are included where copies exist.

## Provenance & attribution

All PDFs were taken from **[DzExams](https://www.dzexams.com/)** — the Algerian
exam-prep library where these sessions are hosted. The original direct
download links were not recorded during collection; the site is credited here
as the source of the copies.

**On republishing:** DzExams publishes no public terms of use or republishing
policy (no terms page on the site, none indexed). The documents themselves are
official Algerian Ministry of National Education BAC exam subjects — state
exam papers distributed publicly for exam preparation and widely
redistributed across Algerian educational sites. BacPack rehosts them
non-commercially for the same purpose (free exam prep), with source credit.

If DzExams or any rights holder objects to this redistribution, contact the
repo owner and the files will be removed or the repository made private
promptly.
