# Étape 4 · Requêtes et concurrents

**But** : savoir ce que les gens cherchent quand ils ont le besoin que le site couvre, quelle page doit répondre
à chaque recherche, et ce que font les concurrents que le client ne fait pas.

## A. Les requêtes

### Où les trouver, dans cet ordre
1. **Suggestions de Google** : taper la requête principale sur google.fr (navigateur), relever les suggestions,
   puis la requête suivie de quelques lettres (a, c, m, p, q…) pour en faire sortir d'autres.
2. **« Autres questions posées »** : dérouler 2 ou 3 questions, d'autres apparaissent.
3. **« Recherches associées »** en bas de page.
4. **Search Console** si l'accès existe : requêtes en position 5 à 20 (gains rapides), requêtes à taux de clic
   anormalement bas (title ou meta à revoir), pages vues sans clic, et requêtes où plusieurs pages du site
   alternent (deux pages qui se concurrencent).
5. **Bing Webmaster Tools** pour des volumes gratuits, si le client a un compte.

### Lire la page de résultats avant de choisir une page
Pour chaque requête retenue, regarder les 10 premiers résultats sur google.fr et noter le **type de page qui
domine** : catégorie, article, fiche produit, vidéo, outil. On produit ce type-là : une fiche produit ne se
classera pas sur une requête où Google ne montre que des guides. Noter aussi les angles des 3 premiers, et
surtout ce qu'aucun des trois ne traite.

### La sortie : 20 lignes au plus
- **1 requête principale**, celle qui résume ce que la marque vend, et sa page cible.
- **8 secondaires au plus** : déclinaisons (usage, matière, zone, type de client). Une page chacune.
- **11 longues au plus** : 4 à 7 mots, une intention précise (« quel X choisir pour débuter », « X ou Y »).

Chaque ligne : intention (information, comparaison, achat, local, marque), page cible existante ou à créer,
volume avec sa source ou `Non vérifié`, et une note de 0 à 5 sur la probabilité qu'une IA reprenne une réponse
à cette question.

### Trois angles de besoin voisin
Partir des problèmes que l'offre résout, pas du produit : chaque problème donne des recherches de gens qui ne
connaissent pas encore la catégorie. Au moins 3, différents des requêtes directes.

### Une requête, une page
Deux pages qui visent la même requête se gênent. Ne parler de ce conflit qu'avec les deux URL nommées et une
preuve (Search Console, ou deux URL du site qui alternent sur la même recherche).

### La répartition des pages
Classer les 20 à 40 pages principales en **information** (guides, FAQ, définitions), **comparaison** (« meilleur
X », « X ou Y », avis) et **achat** (offre, produit, tarifs, contact). Dire sur combien de pages porte le calcul.
Repères repris de la Roso SEO Squad, **non étayés par une étude**, à présenter comme tels :

| Activité | Information / comparaison / achat |
|---|---|
| B2B, SaaS, service B2C, marque personnelle | environ 70 / 20 / 10 |
| E-commerce | environ 50 / 30 / 20 |
| Local | environ 50 / 20 / 30 |
| Média | presque tout en information |

Un site presque sans pages d'information a peu de choses qu'une IA puisse citer. L'étape 6 s'en sert.

## B. Les concurrents

2 à 5, ceux du cadrage, plus ceux qui sortent sur la requête principale (marqués comme tels). On n'analyse pas un
concurrent dont on n'a pas pu lire au moins la page d'accueil : statut « refusé faute de lecture ».

Grille, une colonne par site, le client compris :

| Critère | Comment le vérifier |
|---|---|
| Clarté de l'offre en haut de page | lecture de l'accueil |
| Cible visible | lecture |
| Preuves visibles | accueil + une page offre |
| Pages par offre ou par service | menu + sitemap |
| FAQ | accueil + `/faq` ou équivalent |
| Cas clients, témoignages | accueil + `/clients`, `/references`, `/cas-clients` |
| Avis sur des plateformes | `"concurrent" trustpilot`, G2, fiche Google |
| Présence locale | si pertinent |
| Présence dans les IA | testée à l'étape 7, sinon « non testée » |

Écrire « le concurrent n'a pas de cas clients » demande deux URL testées (règle 3). Jamais de trafic, de nombre
de liens ou d'autorité de domaine sans outil nommé.

**À livrer** : 3 angles qu'aucun concurrent ne couvre (vérifiés chez chacun), les écarts à combler (qui le fait,
et l'action pour le client), et ce que les concurrents font mieux, dit sans détour.

## Note de l'étape

Deux notes : le potentiel des requêtes trouvées, et l'écart avec les concurrents (plus l'écart est grand, plus la
note est basse). La note de l'étape est leur moyenne.

Compte rendu : `4-requetes-concurrents.md`.
