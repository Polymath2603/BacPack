# BacPack

Past **BAC (Algerian baccalauréat) exam papers**, 2008–2025, used by the
[BACBIT](https://github.com/Polymath2603) app's "Past BAC topics" screen.
Papers are downloaded on demand over GitHub raw URLs and cached on device —
nothing is bundled in the APK.

## Layout

```
papers/
  maths/      YYYY-principal.pdf | YYYY-remplacement.pdf | YYYY-rattrapage.pdf
  physics/
  electric/   (Electrical engineering / Technologie)
  english/
  histgeo/    (History & Geography)
  islamic/
```

- `principal` = Main session (June). Filenames are the API contract — don't
  rename without regenerating the app manifest (`tooling/gen_papers_manifest.py`
  in BACBIT).

## How the app uses this

`app/lib/ui/screens/lessons/past_papers_screen.dart` builds its list from
`kPapersBaseUrl = https://raw.githubusercontent.com/Polymath2603/BacPack/main/papers/`
+ `<subject>/<file>.pdf`. Adding a paper = drop the PDF here, push, and
regenerate the manifest. No app release needed for new files with existing
names.

## Adding papers for other subjects / years

1. Name the file `YYYY-principal.pdf`.
2. Put it in the subject folder (create one only if BACBIT's
   `SUBJECTS` map in `gen_papers_manifest.py` is extended too).
3. Push, then run the manifest script so the in-app list picks it up.

## Status

108 papers (6 subjects × 18 years, Main session only — Replacement papers
were removed by decision; they still exist in school/dist/pdf.7z if needed
again). Corrections/solutions are **not** included yet.

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
non-commercially for the same purpose (free exam prep in the BACBIT app),
with source credit.

If DzExams or any rights holder objects to this redistribution, contact the
repo owner and the files will be removed or the repository made private
promptly.
