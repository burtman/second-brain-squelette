# Étape 8 · Cohérence, notes, livrables

**But** : vérifier que l'ensemble tient debout, puis écrire les deux documents que le client lira vraiment. Cette
étape n'ajoute aucun fait : elle trie, hiérarchise et traduit ce que les étapes 1 à 7 ont établi.

## 1. Relecture croisée (obligatoire, avant tout livrable)

Relire tous les comptes rendus d'un bout à l'autre et :
1. lister chaque élément cité dans plus d'un compte rendu (llms.txt, sitemap, LinkedIn, fiche Google, FAQ…) et
   vérifier qu'il a le même statut partout ;
2. chercher chaque mot d'absence (« absent », « aucun », « pas de », « zéro », « à créer », « manquant ») et
   retrouver ses deux preuves ; sans elles, le passer en `Non vérifié` partout où il apparaît ;
3. confronter chaque note à ses constats (un 2/10 en autorité avec deux profils actifs est faux) ;
4. vérifier qu'aucune action ne demande de créer ce qui existe déjà.

En cas de contradiction : retester pour de vrai (curl, recherche), corriger partout, et le consigner. Écrire
`audit-livrables/<slug>/8-coherence.md` : éléments revérifiés, négations revues, contradictions corrigées, ou
« aucune contradiction trouvée ».

## 2. Les notes

| Dimension | Étape | Poids |
|---|---|---|
| Offre et page d'accueil | 2 | 1,5 |
| Technique | 3 | 1,5 |
| Requêtes et concurrents | 4 | 1 |
| Autorité | 5 | 1,5 |
| Contenu | 6 | 1,5 |
| Visibilité IA (le /100 ramené sur 10) | 7 | 1,5 |
| Fiabilité du relevé | 1 | 0,5 |

Note globale = moyenne pondérée, sur 10, avec la mention des étapes à lecture partielle. On ne retouche pas une
note d'étape ici.

## 3. Ce qu'on retient

- **Gains rapides** : impact fort, effort faible ou moyen. 10 au plus, triés par impact puis par effort.
- **Trois axes de fond** (cinq au plus) : pourquoi, concrètement, et ce qu'on doit pouvoir constater à 90 jours
  (un fait mesurable, pas une promesse de position).
- **Feuille de route** : 5 actions cette semaine, 10 sous 30 jours, 10 sous 90 jours. Chaque action vient d'une
  étape et le dit.

## 4. Document 1 · Le Diagnostic (le pourquoi)

Écrit pour un lecteur sans aucune notion de référencement, dans le registre choisi au cadrage.

1. **Le verdict en quatre phrases**, sans aucun terme technique : ce qui va, ce qui est moyen, ce qui bloque,
   par quoi commencer cette semaine. Quelqu'un qui ne lit que ça doit avoir compris.
2. **Trois chiffres** : note globale, score de visibilité IA, et le résultat le plus parlant de l'étape 7
   (par exemple « cité 0 fois sur 22 questions de vos clients »).
3. **Les notes par dimension**, avec une ligne d'explication chacune, puis la part de voix face aux concurrents et
   la tonalité quand la marque est citée.
4. **Les failles**, de la plus grave à la moins grave. Pour chacune : ce qui se passe, la preuve (URL, code,
   extrait), ce qu'on corrige. Un robot de recherche IA bloqué est toujours en tête.
5. **Ce qu'on n'a pas pu vérifier** : chaque `Non vérifié`, pourquoi, et comment le client peut le vérifier en
   une minute. Rien n'y est affirmé.
6. **Où mettre ses efforts** : les sources sur lesquelles la marque a la main, celles où il faut convaincre,
   celles hors de portée pour l'instant (étapes 5 et 7).
7. **Les trois axes de fond** et le plan de contenu.
8. **Par où commencer** : la feuille de route.
9. **Lexique** : uniquement les termes techniques employés dans ce document, traduits (`reference/lexique.md`).

Ton : honnête sans dramatiser. Si c'est mauvais, le dire, puis montrer tout de suite le chemin.

## 5. Document 2 · Le Plan d'exécution (le comment)

Un chantier par action de la feuille de route, dans l'ordre : réparations de la semaine, contenus qui rendent
citable, autorité extérieure, mesure. Chaque chantier a cinq blocs :

1. **Le problème**, en une ou deux phrases, avec les données exactes de l'audit ;
2. **À faire**, à l'impératif ;
3. **Prêt à coller** : pré-rempli avec les vraies données du site, jamais un modèle vide ;
4. **Où le coller**, quand c'est du code : le chemin dans WordPress, Webflow, Wix et Shopify, ou « à déposer à la
   racine du domaine » pour un fichier ;
5. **Vérifier** : comment constater que c'est fait (une URL à ouvrir, un outil à lancer, ce qu'on doit y voir).

Au moins 10 blocs prêts à coller, choisis selon les failles : title et meta ; trois H1 au choix avec leur nombre de
caractères ; paragraphe-réponse sous le bandeau ; réponses corrigées sous les H2 ; réécritures avec des faits ;
JSON-LD corrigé (Organization, LocalBusiness, Person, FAQPage, Article avec `dateModified`) ; `robots.txt` qui
ouvre les robots de recherche IA, laisse Googlebot intact et met l'entraînement en commentaire comme un choix à
trancher ; `llms.txt` ; plan d'article (title, H1, réponse de 50 mots, H2) ; tableau comparatif ; e-mail
d'approche pour un comparatif tiers ; trame de publication LinkedIn ; trame de premier message Reddit ; message de
demande d'avis à envoyer aux clients ; liste des endroits où harmoniser nom, description et coordonnées.

Le dernier chantier est **le suivi mensuel** : trois familles d'indicateurs (Search Console, score de visibilité
IA, autorité), la cible à 90 jours, et la méthode pour refaire le test IA en 15 minutes avec les 5 questions de
l'étape 7.

Le document se termine par une page **« si vous êtes perdu »** : un chantier à la fois, dans l'ordre ; si un bout
de code inquiète, regarder « où le coller » ; si un chantier bloque, passer au suivant ; une fois par mois, refaire
le test. Aucun terme technique sur cette page.

## 6. Mise en forme

- La source fait foi en Markdown : `audit-livrables/<slug>/diagnostic.md` et `plan-execution.md`.
- Pour le client, rendre en HTML (charte du client si on l'a, sinon sobre : fond blanc, un accent, titres nets),
  puis en PDF avec Chrome sans interface :
  ```bash
  "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless --disable-gpu \
    --no-pdf-header-footer --print-to-pdf=Diagnostic_<Client>.pdf diagnostic.html
  ```
- Mesurer le PDF. Au-delà de 1 Mo, il n'entre pas dans le dépôt sans l'accord de l'utilisateur : on garde le HTML
  (qui le régénère) et le PDF part au client sans être committé.
- Avant d'envoyer : un livrable client ne contient ni tiret cadratin, ni « ce n'est pas X, c'est Y », ni terme
  technique non traduit à son premier emploi, ni chiffre sans source.

## 7. Après la livraison

Dans la conversation, jamais dans les documents : proposer d'approfondir un point (détailler l'autorité, dérouler
le plan de contenu sur 6 mois en calendrier, réécrire toutes les réponses sous les H2, comparer page à page avec un
concurrent, transformer la feuille de route en tâches datées, refaire le test IA sur un moteur précis). Un
approfondissement repart des comptes rendus existants et refait des recherches réelles si besoin.

Proposer aussi une date de re-audit (`modes.md`) et, si l'audit concerne un projet suivi dans le vault, une fiche dans
`00-inbox/` pour le suivi, avec son échéance.
