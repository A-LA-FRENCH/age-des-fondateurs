# La jeunesse fait-elle les géants de la tech ?

Étude interactive, en français, sur l'âge des fondateurs au départ et la valeur atteinte par leur société. Elle porte sur 187 « géants » (plus de 10 milliards de dollars de valorisation, fondés de 1968 à 2025) et, dans une seconde partie, sur 278 licornes (plus de 1 milliard).

*English version below.*

## Ce que fait la page

- **Partie 1, les géants** : nuage âge / valorisation, courbe cumulée (part des sociétés et de la valeur créées par des fondateurs de X ans ou moins), distribution des âges, statistiques par tranche, évolution par décennie, répartition par secteur et par région, effet des fondateurs en série, top 25.
- **Partie 2, les licornes** : comparaison licornes de 1 à 10 Md$ et géants, âge selon le niveau de valorisation, nuage, courbe cumulée et distribution.
- Un résumé, une section « ce que dit la recherche », une conclusion et le tableau complet des sociétés, avec recherche et copie en CSV.
- Des filtres valables pour toute la page : mesure de l'âge, période, secteur, région et deux seuils d'âge réglables (26 et 33 ans par défaut). Les chiffres du texte se recalculent avec les filtres.

Tout tient dans un seul fichier, `index.html`. Il suffit de l'ouvrir dans un navigateur, ou d'activer GitHub Pages sur la branche `main`. La page charge D3 depuis cdnjs et ses polices (VT323, IBM Plex Mono) depuis Google Fonts.

## Méthode

- **Âge mesuré.** Par défaut, l'âge du fondateur à la création de sa *première société ayant levé des fonds* (pour Elon Musk : Zip2, 1995, et non SpaceX). Un bouton bascule sur l'âge à la création de la société elle-même. Âge = année de création − année de naissance (± 1 an).
- **Fondateur retenu.** Le cofondateur le plus associé à la société, en général le PDG fondateur.
- **Valorisation.** Maximum atteint, en milliards de dollars courants (non corrigés de l'inflation) : dernier tour privé, prix de rachat ou plus haute capitalisation boursière.
- **Échantillon.** Constitué à la main, non exhaustif. Exclus : filiales et spin-offs de grands groupes, sociétés sans fondateur identifiable, secteurs hors tech. L'échantillon de licornes privilégie les noms connus, ce qui le rajeunit probablement.
- **Âges estimés.** Les valeurs marquées ≈ (champ `approx: 1`) sont incertaines : année de naissance ou première société financée à confirmer.

Ce que l'étude ne mesure pas : un taux de réussite par âge. Il faudrait compter aussi les fondateurs qui ont essayé et échoué. La page cite les travaux qui le font (Azoulay, Jones, Kim et Miranda ; Strebulaev).

## Corriger ou ajouter une société

Les données sont dans le `<script>` de `index.html`, entre les commentaires `// DATA-START` et `// DATA-END`, une société par ligne. Une copie au format CSV est dans `data/societes.csv` ; si vous modifiez l'un, mettez l'autre à jour.

| Champ | Rôle |
| --- | --- |
| `company` | Nom de la société |
| `founded` | Année de création |
| `founder` | Fondateur retenu |
| `birth_year` | Année de naissance du fondateur |
| `first_funded_company`, `first_funded_year` | Première société du fondateur ayant levé des fonds (la société elle-même si c'est la première) |
| `age` | `first_funded_year − birth_year` |
| `age_at_this_company` | `founded − birth_year` |
| `peak_valuation_busd` | Valorisation maximale, en milliards de dollars |
| `tier` | `geant` (≥ 10 Md$) ou `licorne` (1 à 10 Md$) |
| `country`, `region` | Pays d'origine et région (`États-Unis & Canada`, `Chine`, `Europe`, `Reste du monde`) |
| `sector`, `group` | Secteur et famille de secteurs |
| `decade` | Décennie de création, telle qu'affichée |
| `serial` | `true` si le fondateur avait déjà créé une société financée |
| `approx` | `1` si l'âge est une estimation |

Les corrections, avec une source, sont bienvenues par pull request.

## Sources

Recherche : [Azoulay, Jones, Kim, Miranda, « Age and High-Growth Entrepreneurship »](https://www.nber.org/papers/w24489), [Kellogg Insight](https://insight.kellogg.northwestern.edu/article/younger-older-tech-entrepreneurs), [Poets&Quants sur les travaux d'Ilya Strebulaev](https://poetsandquants.com/2023/07/05/do-you-need-an-mba-to-found-a-unicorn-history-says-probably-not/).

Valorisations vérifiées pour 2026 : Nvidia, Apple, Alphabet, Microsoft, Amazon, AMD, SpaceX, Anthropic, OpenAI, Databricks, Stripe, Anduril, Cursor, xAI, Unitree, Polymarket, Lovable, ElevenLabs, Replit. Les liens sont en bas de la page. Les autres valeurs viennent de données publiques connues jusqu'à mi-2026.

---

# Does youth make the tech giants?

An interactive study, in French, of founders' age at the start and the value their company went on to reach. It covers 187 "giants" (valued at more than $10 billion, founded between 1968 and 2025) and, in a second part, 278 unicorns (more than $1 billion).

## What the page does

- **Part 1, the giants**: age / valuation scatter plot, cumulative curve (share of companies and of value created by founders aged X or younger), age distribution, statistics by age bracket, trend by decade, breakdown by sector and region, effect of serial founders, top 25.
- **Part 2, the unicorns**: $1–10B unicorns compared with the giants, age by valuation level, scatter plot, cumulative curve and distribution.
- A summary, a "what the research says" section, a conclusion and the full table of companies, with search and CSV copy.
- Filters that apply to the whole page: how age is measured, period, sector, region and two adjustable age thresholds (26 and 33 by default). The figures in the text update with the filters.

Everything lives in a single file, `index.html`. Open it in a browser, or enable GitHub Pages on the `main` branch. The page loads D3 from cdnjs and its fonts (VT323, IBM Plex Mono) from Google Fonts.

## Method

- **Age.** By default, the founder's age when they started their *first company that raised money* (for Elon Musk: Zip2, 1995, not SpaceX). A toggle switches to the age at the founding of the company itself. Age = founding year − birth year (± 1 year).
- **Founder.** The co-founder most associated with the company, usually the founding CEO.
- **Valuation.** Peak reached, in current billions of dollars (not adjusted for inflation): latest private round, acquisition price or highest market capitalisation.
- **Sample.** Hand-built and not exhaustive. Excluded: subsidiaries and spin-offs of large groups, companies without an identifiable founder, non-tech sectors. The unicorn sample leans towards well-known names, which probably makes it younger.
- **Estimated ages.** Values marked ≈ (`approx: 1`) are uncertain: birth year or first funded company still to be confirmed.

What the study does not measure: a success rate by age. That would also require counting the founders who tried and failed. The page cites the work that does this (Azoulay, Jones, Kim and Miranda; Strebulaev).

## Fixing or adding a company

The data is in the `<script>` of `index.html`, between the `// DATA-START` and `// DATA-END` comments, one company per line. A CSV copy is in `data/societes.csv`; if you change one, update the other. See the field table in the French section above.

Corrections, with a source, are welcome as pull requests.
