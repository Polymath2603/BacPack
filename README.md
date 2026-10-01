# BacPack

Past **BAC (Algerian baccalauréat) exam papers**, 2008–2025, used by the
**BACBIT** exam-prep app's "Past BAC topics" screen. Papers are downloaded on
demand over GitHub raw URLs and cached on device — nothing is bundled in the
APK.

## Layout

```
past-exams/
  index.json              {"subjects": ["arabic", "electric", …]}
  <subject>/index.json    {"files": [{"file": "2008-principal.pdf",
                                        "size": 4825703,
                                        "correction": false}, …]}
  <subject>/YYYY-<session>.pdf
```

Per-subject index entries carry the PDF's `size` in bytes (so the app can show
it before download) and a best-effort `correction` flag (true when the PDF
embeds an official correction/model-answer section — detected heuristically
from PDF text markers and page-count by `gen_papers_index.py`). Older plain
string entries ("2008-principal.pdf") are still valid and the app treats them
as {size: null, correction: false}.

Subjects: `maths`, `physics`, `electric` (Electrical engineering /
Technologie), `english`, `histgeo` (History & Geography), `islamic`,
`arabic`, `french`, `philosophy`, `tamazight`.

- Sessions: `principal` (Main, June) · `remplacement` (Replacement) ·
  `rattrapage` (Second try). Main session is complete for every subject;
  Replacement/Rattrapage are included only where a copy exists (2016–2017).
- Filenames are the API contract — don't rename without regenerating the
  index files.
- Most PDFs embed the official correction sections where the source document
  provided them.

## How the app uses this

The app fetches `past-exams/index.json` to discover subjects, then each
`<subject>/index.json` for the available PDFs — no subject, session, or year
list is hardcoded in the app, so new files appear after a push with no app
update. Display names per language live in the app's string table.

After changing the PDF tree, regenerate the indexes (from the BACBIT repo):
`python3 tooling/gen_papers_index.py`, then commit + push. Requires `pypdf`
for the correction heuristic; without it, `correction` is emitted as `false`.

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
