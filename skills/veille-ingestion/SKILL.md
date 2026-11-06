---
name: veille-ingestion
description: Ingérer une ou plusieurs sources externes (article, PDF, thèse, whitepaper, dump de liens) dans l'espace veille du vault et en sortir une analyse structurée. Utilise ce skill dès que l'utilisateur dit « ingère ça », « ingest raw/xxx », « ajoute ça à la veille », « trouve les sources sur X et range-les », « creuse ce thème », ou dépose un lien/PDF à traiter. Produit : dépôt brut fidèle dans raw/, manifeste SOURCES.md, et une ou plusieurs fiches de veille reliées avec résumé + insights + accords/désaccords + application projet.
---

# Veille — Ingestion → Analyse

Pipeline d'ingestion du second brain. Objectif : transformer des sources brutes en **connaissance reliée et
analysée**, sans jamais polluer la source de vérité ni le wiki. Respecte le contrat du vault (`CLAUDE.md`) et la
**skill `anti-slop.md`** (active en permanence : spécificité > abstraction, chaque idée = mécanisme + mode d'échec).

## Règles cardinales (non négociables)
1. **Ne jamais réécrire `raw/`.** On y *dépose* des copies fidèles, on les *lit*. La synthèse vit dans `03-areas/veille/`.
2. **Ne jamais scanner le vault entier.** Lire à la demande : la fiche-mère du thème, l'index veille, puis les fiches citées.
3. **Veille = matière première triée**, pas le wiki. On *promeut* vers `wiki/` seulement quand un projet la mobilise.
4. **Données sensibles** : vérifier `.gitignore` et la nature des fichiers avant tout `git add`/push (repo privé ≠ tout pousser).

## Le pipeline en 7 étapes

### 1. Cadrage
- Reformuler le **sujet** en une phrase. Identifier **le thème de rangement** = le sous-dossier veille le plus proche
  (ex. `ia-agents/`, `acquisition/`, `economie/`). **Créer un nouveau thème
  seulement si rien ne colle** (et alors ajouter une ligne dans le tableau « Thématiques » de l'index).
- Identifier le(s) **projet(s)** potentiellement servi(s) (ceux listés dans
  `02-projects/`) — sans forcer le lien.

### 2. Collecte
- Si la source est déjà dans `raw/` : la lire. Sinon, `WebSearch` ciblé par **acteur/auteur**, pas par mot-clé générique.
- Trier chaque résultat en 3 bacs :
  - **Primaire** = publié par l'auteur/le fonds/l'institution lui-même (le document de référence). **Prioritaire.**
  - **Secondaire à valeur ajoutée** = décode, chiffre, ou critique avec un mécanisme propre.
  - **Slop** = repost SEO, ferme de contenu, pur hype/CTA, paraphrase sans apport. **À exclure.**

### 3. Filtre slop (le crible)
- Exclure : reposts Medium/agrégateurs, sites SEO (fermes de contenu crypto/IA), threads-pub,
  tout contenu sans donnée ni mécanisme propre.
- **Lister explicitement les exclus** (dans `SOURCES.md` et/ou la note « Contenus exclus » de l'index). Le tri doit être traçable.

### 4. Dépôt brut (`raw/`)
- Créer/choisir `raw/<THEME>/` (nom court, ex. `AI_rollup_theses/`).
- Télécharger des **copies fidèles** : `curl -sL -A "<UA navigateur>"` ; PDF en direct, articles en `.html`.
  Vérifier `HTTP 200` + taille + nombre de mots visibles (`sed 's/<[^>]*>/ /g' | wc -w`) pour écarter les shells JS.
- **Page bloquée (403)** → ne pas committer le dump d'erreur ; créer une **fiche de référence `.md`** reproduisant
  fidèlement les faits captés (datée, marquée « source secondaire fidèle, page non archivable »).
- Créer/mettre à jour **`raw/<THEME>/SOURCES.md`** : tableau primaires / secondaires / **exclus**, avec URL + type.

### 4 bis. Gate de pertinence (évaluer AVANT d'ingérer)
Avant de produire la moindre fiche, juger chaque source sur **deux axes** :
- **Pertinence interne** = qualité intrinsèque du document : *slop* (paraphrase/hype/CTA, aucun mécanisme) ? *promo* (vend un outil/un service, le fond est mince) ? ou *straightforward* (factuel, étayé, mécanisme propre) ?
- **Pertinence externe** = apport *vs le vault existant* : insight réellement nouveau, ou redite de ce qu'on a déjà dans la veille/le wiki ? (Vérifier rapidement la fiche-mère du thème + l'index avant de trancher.)

Décision selon le verdict :
- **Faible valeur ajoutée OU doute** (slop, pure promo, ou rien de neuf vs le vault) → **ne pas ingérer d'office**. Le **signaler** explicitement (dire pourquoi : slop / promo / déjà connu) et **demander confirmation** avant d'ingérer. La source peut tout de même être déposée dans `raw/` + notée comme exclue/à-confirmer dans `SOURCES.md`.
- **Forte valeur ajoutée** (straightforward + insight nouveau) → **ingérer** et **synthétiser les points clés** via les sections d'analyse de l'étape 5.

**Plusieurs documents en même temps : appliquer ce gate UN document à la fois** (évaluer → décider → ingérer ou demander), jamais en masse. Restituer un mini-verdict par document avant de passer au suivant.

### 5. Ingestion → fiche(s) de veille
- Une fiche par sujet atomique (un thème-corpus peut avoir une fiche-mère + des fiches d'approfondissement par source/entité).
- **Frontmatter obligatoire** : `type: source|concept|entity`, `status`, `date`, `tags: []`, `source:` (pointe vers raw).
- **Structure d'analyse imposée** (c'est le livrable — ne pas sauter de section) :
  1. **Résumé par source** — 1 bloc/source : la thèse en une phrase + chiffres/mécanismes concrets (pas de verbe vague).
  2. **Insights clés** — ce qu'on ne savait pas avant, numéroté.
  3. **Points d'ACCORD** — le noyau dur répété par ≥2 sources.
  4. **Points de DÉSACCORD** — les vraies lignes de fracture (qui dit quoi, et pourquoi ça compte). *Section la plus précieuse.*
  5. **Ce qui sert le(s) projet(s)** — application concrète, actionnable, reliée au projet nommé.
  6. **Mode d'échec / limites** quand pertinent.
- **Reliure wikilinks** : chaque fiche relie aux veilles connexes et aux projets via `[[...]]`, même si la cible
  n'existe pas encore (ça marque un sujet à creuser).

### 6. Reliure & index
- Ajouter une ligne dans `03-areas/veille/index.md` (section « Fiches récentes »), avec le thème, le dossier, et le lien projet.
- Poser les **cross-links bidirectionnels** : fiche-mère ↔ fiches d'approfondissement, et vers la/les fiche(s) projet concernées.

### 7. Hygiène repo & push (seulement si demandé)
- `git status` ; vérifier qu'aucun fichier **sensible/non lié** n'est emporté (perso, patrimoine, audit en cours).
- Stager **uniquement** le travail de veille : `03-areas/veille/...` + `raw/<THEME>/`.
- Commit en français, message qui décrit le corpus + les reliures, terminé par `Co-Authored-By: <modèle>`.
- Push sur `main` (cohérent avec l'historique du vault) seulement si l'utilisateur l'a demandé.

## Definition of Done (cocher avant de rendre)
- [ ] Sources primaires identifiées et déposées fidèlement dans `raw/<THEME>/` (+ `SOURCES.md` avec les exclus listés).
- [ ] Gate de pertinence passé par document (interne slop/promo/straightforward + externe nouveau vs vault) ; les sources à faible valeur/douteuses signalées et confirmées avant ingestion.
- [ ] Aucun `raw/` réécrit ; aucun dump d'erreur 403 committé.
- [ ] Fiche(s) avec frontmatter + les 5 sections d'analyse (résumé / insights / accords / désaccords / application projet).
- [ ] Wikilinks bidirectionnels + ligne dans `index.md`.
- [ ] Anti-slop respecté (mécanismes concrets, chiffres, modes d'échec — zéro paraphrase creuse).
- [ ] Si push demandé : rien de sensible/non lié emporté.

## Anti-patterns (à ne pas faire)
- Résumer sans trancher : une fiche sans section **Désaccords** ni **application projet** = du slop documentaire.
- Tout committer parce que « pousse le tout » : pousser ≠ aspirer les fichiers sensibles non liés.
- Garder le slop « pour le volume » : un lien sans mécanisme propre n'entre pas, on le note comme exclu.
- Créer un nouveau thème pour chaque fiche : on range dans l'existant tant que c'est possible.
