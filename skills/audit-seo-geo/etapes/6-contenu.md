# Étape 6 · Contenu citable

**But** : dire quels contenus créer ou retravailler pour que Google les classe et que les IA les reprennent, dans
un rythme que le client peut tenir.

## 1. Inventaire avant toute recommandation

Lister ce qui existe : blog, guides, FAQ, pages par service, comparatifs, pages locales. Avant d'écrire « créer
la page X », tester deux URL plausibles et chercher `site:domaine <sujet>` (règle 3). Recommander une page qui
existe déjà ruine la confiance dans tout l'audit.

## 2. Ce qui rend une page reprenable par une IA

À vérifier sur 3 à 5 pages clés, et à exiger de toute page recommandée :
- **La réponse d'abord** : la réponse à la question de la page dans le premier paragraphe, 40 à 60 mots, une
  phrase de réponse puis deux ou trois de contexte. Jamais après une introduction générale.
- **H2 en forme de question**, chacun suivi d'une réponse de 40 à 60 mots qui tient seule, sans lien dedans.
  Pour chaque H2 qui ne le fait pas : verdict (diluée ou absente) et réponse corrigée prête à coller.
- **Des faits** : chiffres, dates, noms, mesures, résultats nommés, avec leur source quand ils viennent d'ailleurs.
- **Une date** de publication et de mise à jour visibles.
- **Une FAQ** de 6 à 10 vraies questions sur les pages d'offre, réponses de 2 à 4 phrases, la première phrase
  répond.

L'étude GEO de Princeton (Aggarwal et al., arXiv:2311.09735, KDD 2024) a mesuré que l'ajout de citations, de
statistiques et de sources augmente la visibilité d'un texte dans des réponses générées, et que le bourrage de
mots-clés la dégrade. Les pourcentages exacts et leur statut sont dans `reference/chiffres.md`.

## 3. La densité de faits

Sur chaque page clé (hors menu et pied de page) : compter les **faits vérifiables** (chiffre, date, nom propre,
mesure, résultat nommé) et les **généralités** (« leader », « des années d'expérience », « solutions sur mesure »).
Densité = faits pour 100 mots. Repère maison, pas une étude : 1 ou plus, bon ; de 0,5 à 1, moyen ; moins de 0,5,
faible.

Pour chaque page moyenne ou faible, 3 à 5 réécritures avant / après :
> Avant : « Une longue expérience de l'hôtellerie. »
> Après : « [NOMBRE] établissements accompagnés depuis [ANNÉE], dont [CLIENT PUBLIC], [RÉSULTAT MESURÉ]. »

Les crochets restent tant que le client n'a pas donné le vrai chiffre. On n'en invente aucun.

## 4. Couvrir un sujet en entier

Pour chaque sujet pilier tiré de l'étape 4 : au moins 6 angles à couvrir (définition, méthodes, erreurs, coûts,
comparaisons, cas, questions fréquentes…) et le vocabulaire qu'on s'attend à y lire (termes du métier, acteurs,
mesures chiffrées, méthodes). Ce vocabulaire s'intègre dans le texte, jamais en liste plaquée.

## 5. Rééquilibrer la répartition

Si l'étape 4 a montré un déficit (presque toujours en pages d'information), le plan éditorial le comble en
priorité. Moins de contenus, mais bons, plutôt que l'inverse.

## 6. Le plan éditorial

Dimensionné sur le temps que le client déclare pouvoir y passer, pas sur un idéal.
- 30 jours : 8 contenus au plus pour une personne seule. 90 jours : 15 au plus.
- Jamais un rythme quotidien par défaut. Un bon contenu par semaine tenu six mois vaut mieux que trente le premier
  mois et rien ensuite. Plus de volume seulement si le client a une équipe et le demande, présenté comme une option.
- Chaque ligne : sujet, requête visée, page liée, format (celui qui domine la page de résultats, étape 4),
  et la demande d'indexation dans Search Console après publication.

## 7. Règles d'écriture à transmettre avec le plan

Paragraphes de 3 ou 4 lignes ; un seul H1 ; 5 ou 6 H2 par article, pas de H4 ; réponse dans les trois premières
phrases ; images en WebP de moins de 150 Ko, avec un texte alternatif qui décrit l'image et un nom de fichier
lisible ; un ou deux liens internes par article, vers la page d'offre la plus proche, avec un texte de lien qui dit
où il mène (jamais « cliquez ici »).

## Garde-fous propres à l'étape

- Pas de sujet où le client n'a ni expertise ni légitimité visibles.
- Jamais « générer 50 articles avec l'IA ». Tout contenu est relu par un humain qui connaît le métier.
- Pas de FAQ décorative avec des questions que personne ne pose.

Compte rendu : `6-contenu.md`.
