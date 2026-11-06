# Étape 7 · Visibilité dans les IA

**But** : mesurer si les IA citent la marque quand on leur pose les questions de ses clients, qui elles citent à
sa place, et sur quelles sources elles s'appuient. C'est l'étape la plus exposée aux conclusions hâtives : on ne
rapporte que ce qu'on a lu.

## 1. Les questions à poser

20 à 25 questions, écrites comme un vrai client les taperait, dans sa langue et son pays, réparties en cinq
familles :
- **besoin direct** : « quel outil pour faire X », « comment faire X » ;
- **comparaison** : « X ou Y », « alternative à <leader> » ;
- **local**, si pertinent : « meilleur <service> à <ville> » ;
- **problème** : « comment régler <problème> » ;
- **recommandation** : « meilleur <catégorie> pour <profil> ».

Plus 2 questions **de marque** (« que penses-tu de <marque> ? », « <marque> est-il fiable ? »), comptées à part :
elles mesurent la perception, pas la visibilité spontanée.

## 2. Les moteurs

Google (AI Overviews et AI Mode), ChatGPT, Perplexity, Gemini, Claude.

- **Google** : recherche sur google.fr dans le navigateur, `hl=fr&gl=fr`. Noter si un AI Overview s'affiche, si la
  marque y est, et les sources listées. Pas via l'outil WebSearch, qui cherche depuis les États-Unis.
- **ChatGPT, Perplexity, Gemini** : dans le navigateur de l'utilisateur, avec ses sessions connectées, selon le niveau choisi au
  cadrage. Une nouvelle conversation par question, sans contexte préalable.
- **Claude** : un sous-agent neuf, sans aucun contexte, qui reçoit la question seule et peut chercher sur le web.
  L'étiqueter « Claude via Claude Code, recherche depuis les États-Unis », ce qui n'est pas exactement ce que voit
  un utilisateur de claude.ai en France. Si la précision compte, poser la question sur claude.ai dans le navigateur.

## 3. Trois niveaux, choisis au cadrage

| Niveau | Ce qu'on fait | Coût | Marge d'erreur annoncée |
|---|---|---|---|
| **Live complet** | toutes les questions, sur tous les moteurs | ~75 requêtes, une bonne heure | ±5 |
| **Live ciblé** | Google et Claude sur toutes ; les 5 questions décisives en live sur ChatGPT, Perplexity et Gemini ; le reste par triangulation, recalé sur l'écart observé entre live et triangulation | ~25 requêtes | ±10 |
| **Sans live** | Google et Claude sur toutes ; ChatGPT, Perplexity et Gemini par triangulation | faible | ±12 si la triangulation tient, ±20 sinon |

Ces marges sont une convention de lecture, pas un intervalle statistique. On les écrit telles quelles.

**Questions décisives** : forte intention d'achat ou de comparaison, marque « sur le fil », concurrent sans doute
mieux placé, ou résultats très différents d'un moteur à l'autre.

**Triangulation** (quand un moteur n'est pas testé en direct), pour chaque question : lire la page de résultats
google.fr, ouvrir les sources qui reviennent (comparatifs, fils Reddit et forums, médias), et vérifier si la marque
et les concurrents y figurent. Au moins 3 sources lues pour parler d'estimation ancrée. Une triangulation qui ne
trouve rien conclut « marque non observée dans les sources de cette question », jamais « absente de ChatGPT ».

## 4. Noter chaque réponse

| Points | Quand |
|---|---|
| 0 | la marque n'apparaît pas |
| 1 | la marque est mentionnée |
| 2 | la marque est citée nommément avec un lien ou comme source |

Pour chaque réponse lue, noter aussi : les concurrents nommés, les domaines cités en source, et, si la marque
apparaît, la **tonalité** (favorable, neutre, réservée, défavorable) avec une paraphrase courte qui la justifie.
Jamais de longue citation de la réponse, jamais de tonalité sur une ligne estimée.

**Questions de suivi**, en live seulement : sur 3 à 5 questions décisives, enchaîner une ou deux relances
naturelles dans la même conversation (« lequel tu recommandes ? », « et pour un petit budget ? »), sans glisser le
nom de la marque. Noter si elle apparaît, disparaît ou monte.

## 5. Les chiffres qui sortent de l'étape

- **Score de visibilité IA sur 100** : par moteur, points obtenus divisés par points possibles. Score global
  pondéré : Google 25, ChatGPT 25, Perplexity 20, Gemini 15, Claude 15. Toujours avec la marge du niveau choisi
  et la mention de ce qui a été testé en direct.
- **Part de voix** : sur les réponses **réellement lues** seulement, citations de la marque divisées par le total
  des citations de marques. Donner le dénominateur. Un concurrent jamais cité vaut 0, on ne le gonfle pas.
- **Niveau** : absente (citée nulle part après test réel sur au moins deux moteurs), émergente (sur moins de 10 %
  des questions), partielle (10 à 30 %, souvent un seul moteur), installée (plus de 30 % sur au moins deux moteurs).
- **Sources manquantes** : les domaines cités quand la marque est absente, triés par fréquence, chacun classé
  direct, indirect ou hors de portée (étape 5, section 5), avec l'action.

## 6. Ce qui empêche d'être cité

Croiser avec les étapes précédentes, dans cet ordre :
1. un robot de recherche IA bloqué (étape 3) passe avant tout le reste : améliorer une page qu'aucune IA n'a le
   droit de lire ne sert à rien ;
2. les comparatifs tiers et les plateformes où les concurrents sont et pas la marque (étape 5) ;
3. les pages sans réponse directe, sans faits, sans date (étape 6) ;
4. l'entité floue : nom ou description différents selon les sources (étape 5).

## 7. Sorties

- Le tableau des questions : une ligne par question, une colonne par moteur, avec la mention « live » ou
  « triangulé ».
- Part de voix, tonalité, suivis, sources manquantes.
- La feuille de route : 5 actions sur 7 jours, 10 sur 30 jours, 10 sur 90 jours au plus, chacune avec l'étape
  d'où elle vient.
- **5 questions que le client peut retester seul**, une IA chacune, avec le lien, ce qu'il doit regarder, et la case
  à mettre à jour. Elles servent de point de départ au re-audit.

Aucun délai de citation promis. Une marque créée il y a moins de 6 mois : prévenir que la mesure sera surtout
une référence de départ.

Compte rendu : `7-visibilite-ia.md`, avec `grille-ia.md` (le tableau complet) à côté.
