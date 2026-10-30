# Mauritania: law history in git

The law of Mauritania as a git history: one file per provision, one commit per law or decision on the day it took effect, and the law that made each change as the commit's author. `git blame` names the law behind every paragraph; `git log` lists every change to a provision; `tools/on.py` gives the text in force on any day.

It follows the shared design of [lexifina/global-law](https://github.com/lexifina/global-law), which places it at `mr/`.

> **First build.** The text is the consolidated Constitution published by the Ministry of Finance of Mauritania (finances.gov.mr). This first build holds one version of the Constitution; statutes are added below.

Language: the text is in French (the official language of the published text); this README is in English.

**What is in it now**

| Folder | Act | Versions | History |
| --- | --- | ---: | --- |
| `constitution/` | Constitution de la République islamique de Mauritanie (1991, révisée jusqu'en 2017) | 1 | Oldest version available, dated 15 August 2017, the day of the constitutional laws n° 2017-021 and 2017-022 named in the text's title (102 articles) |
| `code-penal/` | Code pénal (ordonnance n° 83-162 du 9 juillet 1983) | 1 | Oldest version available: the 1983 ordinance as published, dated 29 February 1984, with no later amendments (451 articles) |
| `code-de-commerce/` | Code de commerce (loi n° 2000-05 du 18 janvier 2000, modifiée par la loi n° 2015-32) | 1 | Oldest version available: the consolidated text, dated 30 November 2015, the day the 2015 amendments took effect (1546 articles) |
| `code-du-travail/` | Code du travail (loi n° 2004-017 du 6 juillet 2004) | 1 | As enacted, dated 6 July 2004, with no later amendments (452 units) |

## Questions as git commands

| Question | Command |
| --- | --- |
| The whole act on a date | `python tools/on.py 2024-01-01 constitution` |
| One provision on a date | `python tools/on.py 2024-01-01 constitution <unit>` (unit = file name without `.md`) |
| Which law wrote each line of a provision? | `git blame constitution/<unit>.md` |
| Every change to a provision, word by word | `git log -p --word-diff constitution/<unit>.md` |
| Every law in the record, in order | `git log --reverse --format="%ad %an" --date=short main` |

After a rebuild, refresh tags with `git fetch --force --tags`: a plain fetch keeps stale tags.

## What it does not show

- **One version.** The Ministry publishes only the consolidated text. The 1991, 2006 and 2012 texts and the amending laws are not shown as separate versions; the single version is dated 15 August 2017 and credited to the publisher ("oldest version available").
- **Headings and paragraphs.** Titre headings are left out, the "(nouveau)" marker after an article number is dropped, and paragraph breaks are rebuilt from the PDF line layout, so a few paragraphs may be joined that print separates.
- **Code pénal.** The text is the 1983 ordinance as published, not a consolidation: later amendments (for example article 306 in 2018) are not applied. Headings (Livre, Titre, Chapitre, Section) are left out and paragraph breaks are rebuilt from the PDF line layout.
- **Code de commerce.** The text is the consolidated version as amended by loi n° 2015-32; the 2000 original and the amending law are not separate versions. Headings are left out, and articles are split on the printed markers in a PDF where they run together.
- **Code du travail.** The text is loi n° 2004-017 as enacted. Later amendments, including loi n° 2022-025 (articles 38, 417, 418, 449 and 436), are not applied. Article 98 is printed twice in the source; both are kept, the second as `art-098-dup2`. Headings are left out.

## How it is built

Lexifina reads the sources listed here and records each act's dated versions, and the laws that made each change, in one corpus file. `tools/build.py` writes this repository from that file, and the same corpus always gives the same commit hashes; `REPRODUCE.md` gives the details and the checks. A model (Claude) wrote Lexifina's code; it wrote no legal text, and no model runs when the history is built.

Lexifina's code reads the PDF text layer with PyMuPDF and writes `corpus.json`; Lexifina's code does the same for each statute and writes one part file in `corpus.d/`. The shared builder turns `corpus.json` into the commits; `REPRODUCE.md` lists the sources, commands and decisions, and the result of the checks (every version read back from git on its in-force day and the day before, trailers parsed, no merge commits, dates never going backwards).

## Sources

| Source | What | Notes |
| --- | --- | --- |
| [Ministère des Finances](https://finances.gov.mr/Recueil_des_textes_relatifs_a_la_mission_du_Ministere/Textes/TXT%20GL/Constitution%20de%20la%20RIM.pdf) | Constitution, consolidated PDF with a text layer | No licence stated. |
| [WIPO Lex](https://www.wipo.int/wipolex/edocs/lexdocs/laws/fr/mr/mr004fr.pdf) | Code pénal, text-layer PDF (MR004) | Official text republished by WIPO Lex. No licence stated. |
| [WIPO Lex](https://wipolex-res.wipo.int/edocs/lexdocs/laws/fr/mr/mr028fr.pdf) | Code de commerce, consolidated text-layer PDF (MR028) | Official text republished by WIPO Lex. No licence stated. |
| [Ministère des Finances](https://finances.gov.mr/Recueil_des_textes_relatifs_a_la_mission_du_Ministere/TEXTES/EMPLOI/Loi%202004-017%20C%20Trav.pdf) | Code du travail, text-layer PDF | Official text published by the Ministry. No licence stated. |

See `LICENSE` for the attribution.
