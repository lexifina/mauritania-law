# How this repository was made (Mauritania)

This file is written by the build on 2026-10-30, the day the source data was retrieved.

## Sources

| Source | Address | Retrieved | Licence |
| --- | --- | --- | --- |
| Ministère des Finances: Constitution de la République islamique de Mauritanie (PDF) | <https://finances.gov.mr/Recueil_des_textes_relatifs_a_la_mission_du_Ministere/Textes/TXT%20GL/Constitution%20de%20la%20RIM.pdf> | 2026-10-29 | no licence stated; consolidated text of the Constitution published by a ministry |
| WIPO Lex: Ordonnance n° 83-162 du 09 juillet 1983 portant institution d'un Code pénal (MR004) | <https://www.wipo.int/wipolex/edocs/lexdocs/laws/fr/mr/mr004fr.pdf> | 2026-10-30 | official text of law republished by WIPO Lex; no licence stated on the PDF |
| WIPO Lex: Loi n° 2000-05 du 18 janvier 2000 portant Code de commerce, telle que modifiée par la loi n° 2015-32 (MR028) | <https://wipolex-res.wipo.int/edocs/lexdocs/laws/fr/mr/mr028fr.pdf> | 2026-10-30 | official text of law republished by WIPO Lex; no licence stated on the PDF |
| Ministère des Finances (Mauritanie): Loi N° 2004-017 portant code du travail (PDF) | <https://finances.gov.mr/Recueil_des_textes_relatifs_a_la_mission_du_Ministere/TEXTES/EMPLOI/Loi%202004-017%20C%20Trav.pdf> | 2026-10-30 | official text of law published by the Ministry of Finance; no licence stated on the PDF |

Every word of law in this repository comes from these sources. Lexifina reads them and records each act's dated versions, and the laws that made each change, in one corpus file. This repository is built from that file.

## What is in it

| Act | Title | Versions | Span |
| --- | --- | ---: | --- |
| `constitution` | Constitution de la République islamique de Mauritanie (1991, révisée jusqu'en 2017) | 1 | 2017-08-15 to 2017-08-15 |
| `code-penal` | Code pénal (ordonnance n° 83-162 du 9 juillet 1983 portant institution d'un Code pénal) | 1 | 1984-02-29 to 1984-02-29 |
| `code-de-commerce` | Code de commerce (loi n° 2000-05 du 18 janvier 2000, telle que modifiée par la loi n° 2015-32 du 10 septembre 2015) | 1 | 2015-11-30 to 2015-11-30 |
| `code-du-travail` | Code du travail (loi n° 2004-017 du 6 juillet 2004 portant Code du travail) | 1 | 2004-07-06 to 2004-07-06 |

The build made 4 commits:

| Commits | Kind |
| ---: | --- |
| 4 | first version of an act |
| 0 | one law on its in-force day |
| 0 | changes no amendment note explains, credited to the publisher |

Other counts:
- 0 commits on the branch `future`: laws not yet in force on 2026-10-30.
- 0 commits dated 1 January 1970: in force before 1970, with the real day in their `In-force` trailer.
- 1 laws in the record.
- 5 tags.

## Dates

Each commit is dated at noon (Africa/Nouakchott) on the day the change took effect. The other dates, enacted and published, are trailers.

When a law gives no date of its own, the default rule applies: La loi constitutionnelle référendaire n° 2017-022 du 15 août 2017 est promulguée le 15 août 2017; the consolidated text is dated by it. https://finances.gov.mr/Recueil_des_textes_relatifs_a_la_mission_du_Ministere/Textes/TXT%20GL/Constitution%20de%20la%20RIM.pdf

## How the history is built

`tools/build.py` turns the corpus into this history in one pass: one commit per law, on the day it took effect. The same corpus always gives the same commit hashes. `tools/check_repo.py` reads every version back from git and compares it with the corpus. `tools/on.py` shows the law as it stood on any date. The corpus format is described in `tools/SCHEMA.md`.

- Corpus: sha256 `494ca31ccff9de84cfca34ccf35793c7633629c22f3a7df332f0ebeaced44c85` (1789365 bytes).
- Builder blob hashes (`git hash-object`): `build.py` `a4faa25af85facb64b956b372f6b528aafdd7ec1`, `check.py` `3d00541d258745461ab52b1b0cb4e1716a27a95d`, `on.py` `644a6c0857fbcc72562032b58d57aa113fee0641`.
- Python 3.12.10; git version 2.46.0.windows.1.

## Checks

4 versions of 4 acts read back from git on the day each took effect and on the day before: 0 mismatches. Trailers: 0 commits whose trailers git cannot parse. Health: 0 merge commits on main, 0 commit dates that go backwards, 0 commits dated after the build.

A second build from the same corpus into an empty folder gave identical hashes for all 4 history commits and 5 tags (history tip `5a47b247dce7c89e5cd6fcb7c9e2ecfb5947b086`).

## Decisions made by hand

- French is the official language of the published text; it is built in French.
- One version, the oldest available (first_law null), credited to the Ministry of Finance as publisher. The PDF gives no date of its own; its title names the latest amending laws (n° 2017-021 and 2017-022 of 15 August 2017), so it is dated 2017-08-15.
- The earlier texts (1991, 2006, 2012) and the individual amending laws are not built.
- Unit files: the preamble and one per article (art-NNN, 1-102; art-001 is "Article premier"); Titre headings are left out; the "(nouveau)" marker after an article number is dropped; paragraph breaks are rebuilt from the PDF line layout (a short line ending in . ; or : ends a paragraph; list items start new lines).
- Code pénal: one version, the oldest available (first_law null), the 1983 ordinance as published, dated 1984-02-29 (the Journal officiel number in which WIPO Lex gives it entering into force). It is not a consolidation: later amendments are not applied.
- Code pénal units: one per article (art-001 is "Article premier"); Livre, Titre, Chapitre, Section and paragraph headings are left out; paragraph breaks are rebuilt from the PDF line layout.
- Code de commerce: one version, the consolidated text as amended by loi n° 2015-32, dated 2015-11-30 (the day that amending law entered into force, per WIPO Lex). The original 2000 text and the 2015 law are not shown as separate versions.
- Code de commerce units: one per article (art-NNN, with -bis/-ter/-quater suffixes as printed); Livre, Titre, Chapitre, Section headings are left out; the "(Loi n° 2015-32)" markers printed in the consolidated text are kept as part of the article text.
- Code du travail: one version, the Code as enacted (first_law loi n° 2004-017), dated 2004-07-06, the date of the law as cited by loi n° 2022-025. The PDF prints the adopting formula and article 451, which orders publication by the urgent procedure, but no date; it was made in March 2005 and its fines are in old ouguiyas, so it is the 2004 text with no later amendments.
- Code du travail: later amendments are not applied. Loi n° 2022-025 of 29 November 2022 (articles 38, 417, 418 and 449 replaced, article 436 repealed) cites the Code as "modifiée", so earlier amending laws also exist; without them a consolidated later version cannot be built.
- Code du travail units: one per article (art-001 is "Article 1er"), with the article title as printed on the line after the number. Livre, Titre, Chapitre and Section headings, running heads, page numbers, the table of contents and the signatures are left out.
- Code du travail: article 98 is printed twice (the second, in Chapitre V, stands where article 99 should be; the table of contents gives Chapitre V as article 99). Both are kept as printed; the second is art-098-dup2. The unnumbered paragraph that opens Livre VII is kept as art-386-texte.
- Code du travail: words broken at a line end are rejoined; the hyphen is kept only where the hyphenated form is printed unbroken elsewhere in the Code (celle-ci, ci-dessus, sous-entreprise, peut-être, vingt-cinq). Every paragraph was checked against the PDF text, and every body line of the PDF is in a unit except the signatures.

## What AI did and did not do

The scripts that read the sources and build this repository were written by Claude Code running Claude Opus 5.5 (`claude-opus-5-5`) under Lexifina's direction.

No model wrote, translated or corrected legal text. No model runs at build time. Every word of law in this repository comes from the official sources above.

The commit messages are written by `build.py` from the source data.

Model use at data-build time:
- Claude Code wrote the code and chose the source; it did not write or alter any legal text. The code is deterministic and runs no model.
- Claude Code wrote the code and chose the source; it did not write or alter any legal text. The code is deterministic and runs no model.
- Claude Code wrote the code and chose the source; it did not write or alter any legal text. The code is deterministic and runs no model.
- Claude Code wrote the code and chose the source; it did not write or alter any legal text. The code is deterministic and runs no model.
