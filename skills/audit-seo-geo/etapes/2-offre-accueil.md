# Étape 2 · Offre et page d'accueil

**But** : comprendre ce que le site promet, à qui, et vérifier que la page d'accueil le dit vite et clairement,
pour un humain, pour Google et pour une IA.

## A. L'offre

À partir de `fiche-site.md`, de la page « à propos » et de la page tarifs si elles existent, et d'une recherche
de la marque pour voir comment d'autres la décrivent :

- **Promesse actuelle**, citée mot pour mot, avec l'URL. Si aucune phrase ne la porte, l'écrire.
- **Lecture** : ce qui est clair, ce qui est flou, ce qui manque.
- **Cible** : une cible principale, une ou deux secondaires.
- **Trois formulations de promesse**, chacune sur ce gabarit complet :
  « Pour <qui>, qui veut <résultat>, <marque> est <catégorie> qui <différence>, contrairement à <alternative>. »
  Les différences viennent de ce qui est visible ou prouvable, jamais d'un superlatif.
- **Objections** : 5 au plus, chacune avec la réponse à afficher sur le site.
- **Preuves à ajouter** : chiffres, cas, logos, certifications. Si la donnée réelle manque, un emplacement
  explicite `[CHIFFRE RÉEL À FOURNIR]`, jamais un chiffre plausible.

Ici on ne parle pas mots-clés : c'est l'étape 4.

## B. La page d'accueil

Pour chaque élément : valeur exacte, mesure, source (curl, navigateur, extrait Google, copier-coller).

| Élément | Repère de praticien |
|---|---|
| Title | 50 à 60 caractères, la requête principale dans les premiers mots |
| Meta description | 140 à 160 caractères, un bénéfice et une incitation |
| H1 | un seul, moins de 65 caractères, porte la requête principale ; à ne pas confondre avec le title |
| Bandeau du haut | en 3 secondes on sait qui, pour qui, quel bénéfice ; 20 à 50 mots |
| Bouton principal | un seul visible sans défiler, un verbe d'action |
| Preuve visible sans défiler | au moins une : avis, logos, chiffre, certification |
| Titres | H1, puis H2, puis H3, sans saut de niveau |
| Premier paragraphe | 40 à 60 mots qui répondent à « qui, quoi, pour qui », placé tôt dans la page |
| Sous chaque H2 en forme de question | une réponse de 40 à 60 mots qui tient seule, sans lien dedans |
| Confiance | page à propos, contact, mentions légales, personnes nommées |

Un title « trop court » se prouve avec son nombre exact de caractères. Un « H1 absent » se prouve deux fois
(règle 3 de `regles.md`), parce qu'un H1 masqué ou injecté en JavaScript échappe souvent à curl.

**Livrer aussi** :
- un bandeau réécrit : H1, sous-titre, bouton principal, bouton secondaire, preuve à afficher. Uniquement le
  bandeau, pas toute la page. Si le bandeau actuel n'a pas pu être lu, le dire ;
- pour chaque H2-question qui ne répond pas d'emblée, la réponse de 40 à 60 mots corrigée, prête à coller.

## Note de l'étape

Une note pour l'offre (clarté et différence) et une pour la page d'accueil ; la note de l'étape est leur moyenne.
Avec une fiche du site provisoire, 6 au plus.

Compte rendu : `2-offre-accueil.md`.
