# Structure

| Dossier | Contenu |
| --- | --- |
| `constitution/` | La Constitution du 20 juillet 1991, révisée jusqu'en 2017 |
| `codes/<code>/` | Les codes : `codes/code-penal/`, `codes/code-de-commerce/`, `codes/code-du-travail/` |
| `lois/<année>/<numéro>-<objet>/` | Les lois (lois, lois organiques, lois de finances), par année et numéro, p. ex. `lois/2018/2018-039-abrogeant-et-remplacant-la-loi-n78-011-du-19/` |
| `ordonnances/<année>/<numéro>-<objet>/` | Les ordonnances, p. ex. `ordonnances/1983/83-127-portant-reorganisation-fonciere-et-domaniale/` |
| `decrets/<année>/<numéro>-<objet>/` | Les décrets |
| `arretes/<année>/<numéro>-<objet>/` | Les arrêtés (ministériels, interministériels, conjoints) |
| `decisions/<année>/<numéro>-<objet>/` | Les décisions réglementaires de l'Autorité de Régulation (CNR) |

Chaque dossier de texte contient un fichier par article (`art-001.md` est l'article premier, `art-012-bis.md`
l'article 12 bis), `visas.md` (les visas), `signatures.md` (la formule finale et les signatures), et un `README.md`
qui donne la source, la date retenue et la nature de la couche texte. Un texte où aucun article n'est repéré est
conservé en un seul fichier, `texte-integral.md`. Aucun dossier ne contient plus de 1 000 entrées.

Le texte arabe officiel d'un texte, quand il est publié avec une couche texte lisible, est dans `<texte>/ar/` (même découpage : `art-NNN.md`, `visas.md`, `README.md`) ; un texte connu seulement en arabe a son dossier nommé par nature, année et numéro, avec le texte dans `ar/`.

## Dates

Chaque version est un commit daté à 12 h 00, heure de Nouakchott (UTC+0), du jour où elle a pris effet, que répète
le trailer `In-force:` ; `In-force-basis:` dit d'où vient ce jour :

- pour les textes repris depuis le Recueil du Ministère des Finances, FAOLEX ou WIPO Lex : la date du texte dans son
  intitulé (promulgation ou signature), le texte étant exécutoire dès sa promulgation faute d'autre clause ; ces
  sources ne donnent pas le jour de publication au Journal officiel ;
- pour les versions de l'ancienne construction (Constitution, codes, statut général des fonctionnaires) : les dates
  que donnent leurs commits.

Avant 1970, que git ne sait pas dater, un commit est daté du 1er janvier 1970 ; le jour réel figure dans son objet et
dans `In-force:`. Aucune date de ce dépôt n'est celle à laquelle nous avons téléchargé un fichier.

## Trailers

`In-force`, `In-force-basis`, `Source` (le PDF), `Text-layer` (`born-digital` ou `publisher-ocr`), `Version`, et pour
les copies secondaires `Source-status: secondary copy (FAOLEX, …)` ; `Text-source: publisher OCR` quand la couche texte
est celle qu'un éditeur a posée sur un document numérisé (nous ne faisons aucun OCR).
