---
type: skill
status: active
date: 2026-06-25
tags: [skill, idéation, créativité, méthodes]
source: https://github.com/NousResearch/hermes-agent/blob/main/optional-skills/creative/creative-ideation/SKILL.md
author: SHL0MS (NousResearch/hermes-agent)
---

# Creative Ideation — Bibliothèque de méthodes

Skill de routage : quand l'utilisateur veut générer des idées, choisir entre options, ou se débloquer, suivre cette procédure plutôt que de brainstormer librement.

## Quand activer

- "Je veux créer / construire / écrire / lancer quelque chose"
- "Je suis bloqué", "inspire-moi", "rends ça plus bizarre"
- "Aide-moi à choisir", "j'ai besoin d'inventer X"
- "Que pourrais-je faire ?"

## Règles opérationnelles

1. **Contrainte + direction = créativité.** Sans contrainte = pas de traction. Sans direction = pas de forme. Les méthodes fournissent les deux.
2. **Refuser les 3 premières idées.** C'est du slop. Générer → jeter → regénérer. Voir [[anti-slop]].
3. **Une méthode par réponse**, sauf demande explicite de stacking.
4. **Spécificité > abstraction.** Noms propres réels, mécanismes concrets. "Une app pour X" = slop ; "un outil CLI de 200 lignes qui fait Y quand Z" = direction.
5. **Le bizarre doit aussi être bon.** Chaque set doit inclure au moins une idée *réalisable maintenant*.
6. **Nommer la méthode utilisée** et son inventeur. L'attribution active la discipline.
7. **Quand l'utilisateur choisit, construire.** Ne pas continuer à générer après un choix.

---

## Procédure de routage (4 étapes)

Faire avant toute génération. Le routing raté produit du slop.

### Étape 1 — Extraire 3 signaux

**PHASE — où en est l'utilisateur ?**

| Phase | Indices |
|---|---|
| GÉNÉRER | "donne-moi une idée", "qu'est-ce que je devrais faire" — pas d'idée encore |
| ÉLARGIR | "quoi d'autre", "des variations" — a une idée de base |
| SÉLECTIONNER | "aide-moi à choisir", "j'ai ces options" |
| DÉBLOQUER | "je suis bloqué", "je tourne en rond" — a du matériel |
| SUBVERTIR | "rends ça plus bizarre", "moins évident", "trop safe" |
| AFFINER | "c'est bien mais il manque quelque chose" |
| SYNTHÉTISER | "j'ai une pile de notes / interviews / observations" |
| DIAGNOSTIQUER | "qu'est-ce qui est vraiment porteur ici ?", "où ça va casser ?", stress-test d'un système existant |

**DOMAINE — qu'est-ce qu'on fait ?**

| Domaine | Cues |
|---|---|
| TEXTE | fiction, essai, poème, paroles, script, copywriting |
| OBJET | art visuel, musique, performance, installation, sculpture |
| ARTEFACT | logiciel, hardware, mécanisme, device |
| SYSTÈME | org, civic, institution, écologie, communauté |
| SOI | décision de vie, carrière, pratique personnelle |
| RECHERCHE | papier, thèse, question de recherche |
| PRODUIT | business, marché, service |

**SPÉCIFICITÉ — combien de contrainte dans le prompt ?**

| Niveau | Indices |
|---|---|
| AUCUNE | "j'ai envie de faire quelque chose" — pas de domaine, pas de projet |
| DOMAINE | "je veux écrire quelque chose" — connaît le champ, pas de projet |
| PROJET | "je travaille sur ce X précis" |
| PROBLÈME | "j'ai cette friction spécifique dans X" |

### Étape 2 — Vérifier les surcharges (priorité max)

Ces règles écrasent le tableau de routage :

- **Signal de mood** — "bizarre", "étrange", "surprenant", "moins évident", "plus intéressant" → forcer **Provocations latérales** ou **Pataphysique**, peu importe le domaine
- **L'utilisateur nomme une méthode** → l'utiliser
- **Demande de recommandation de méthode** → proposer 2-3 candidats avec une ligne chacun, demander lequel appliquer
- **Terrain à fort slop** — "idées IA", "idées startup", "app productivité/bien-être/fitness/voyage" → forcer **Provocations latérales** ou **Pataphysique** + refuser les **5** premières idées (pas 3)

### Étape 3 — Router par phase puis domaine

**Par phase (peu importe le domaine) :**

| Phase | Méthode par défaut |
|---|---|
| GÉNÉRER + SPÉCIFICITÉ=AUCUNE | Dispatch par contrainte (prompt aléatoire du catalogue) |
| GÉNÉRER + domaine connu | → tableau domaine ci-dessous |
| ÉLARGIR | **SCAMPER** (Substitute, Combine, Adapt, Modify, Put to other use, Eliminate, Rearrange) — pour faire varier *une* pièce précise, voir **Substitution d'entités** (méthode locale) |
| SÉLECTIONNER | **Pré-mortem et inversion** |
| DIAGNOSTIQUER | **Substitution d'entités**, mode diagnostic (méthode locale) — substituer pour révéler ce qui est porteur / dé-risquer |
| DÉBLOQUER | **Stratégies obliques** (Brian Eno / Peter Schmidt) |
| SUBVERTIR | **Provocations latérales** (de Bono) → fallback : **Pataphysique** |
| AFFINER (texte) | **Défamiliarisation** (Chklovski) |
| AFFINER (autre) | **Discipline créative** (Tharp — trouver la colonne vertébrale) |
| SYNTHÉTISER | **Diagrammes d'affinité** (Kawakita Jiro) |
| Volume rapide nécessaire | **Génération par volume** (100 idées en 10 min, filtrer ensuite) |

**Par domaine (si GÉNÉRER + domaine connu) :**

| Domaine | Méthode par défaut |
|---|---|
| TEXTE — formel / poésie | **OuLiPo** (contraintes formelles : Perec, Queneau) |
| TEXTE — narratif | **Squelettes narratifs** (structure archétypale) |
| TEXTE — du matériel source à remixer | **Chance et remix** (Burroughs, Cage) |
| OBJET (musique, visuel, performance) | **Stratégies obliques** (Brian Eno) |
| OBJET — maker physique | Dispatch par contrainte — section Physique/Objet |
| ARTEFACT — contrainte de départ | Dispatch par contrainte — section Software/Artefact |
| ARTEFACT — conflit de paramètres d'ingénierie | **TRIZ** (principes d'invention) |
| ARTEFACT — architecture logicielle | **Langages de patterns** (Christopher Alexander) |
| ARTEFACT — analogue naturel disponible | **Biomimétisme** |
| ARTEFACT — hypothèses accumulées à questionner | **Premiers principes** (Musk / Aristote) — version opérationnelle (Idiot Index + algo 5 étapes) en méthode locale |
| Tout problème de coût / config héritée (tout domaine) | **Premiers principes** opérationnels (méthode locale) — Idiot Index + supprimer avant d'optimiser |
| Problème qui semble neuf | **Transfert analogique** (invariant, méthode locale) avant de réinventer |
| SYSTÈME (civic, org, institutionnel) | **Leverage points** (Donella Meadows) |
| SYSTÈME — collectif / participatif | Dispatch — section Social/Collectif |
| SOI (vie, carrière, que-étudier) | **Dérive et cartographie** (Debord / situationnisme) |
| RECHERCHE — choisir une question | **Compression-progrès** (identifier la frontière de la connaissance) |
| RECHERCHE — attaquer un problème connu | **Polya** (heuristiques de résolution) |
| PRODUIT (business, service) | **Jobs-to-be-done** (Christensen) |
| PRODUIT — tu es sur le point d'inventer une confiance / un label / une certification | **Arbitrage d'autorité latente** (généralisation TRIZ-IFR — voir méthode locale en bas) |
| Besoin de briser un cadre / trouver une analogie | **Analogie et blending** |

### Étape 4 — Gérer l'ambiguïté

- **Plusieurs chemins plausibles** → prendre le plus proche de la formulation exacte de l'utilisateur. Ne pas choisir la méthode la plus intéressante pour paraître sophistiqué.
- **Vraiment ambigu** → poser UNE question de clarification. Ex : *"Tu génères des idées ou tu choisis parmi des options existantes ?"*
- **Signaux contradictoires** (ex : "idées startup bizarres" → domaine produit + signal bizarre) → **empiler deux méthodes explicitement** en le disant : *"J'utilise Jobs-to-be-done pour le cadrage produit + Provocations latérales pour briser la forme évidente."*
- **Même question reposée** → changer de méthode. Variation de méthode = variation de distribution des idées.

### Check anti-défaut (avant de générer)

- Vais écrire "Voici 5 idées :" suivi d'une liste ? → **STOP.** Choisir une méthode d'abord.
- Vais brainstormer librement sans méthode ? → **STOP.** Trouver le bon chemin dans le tableau.
- L'output ressemble à ce qu'un LLM non-routé produirait ? → **Routing raté**, recommencer.

---

## Format de sortie

Pour le chemin par défaut (dispatch par contrainte) :

```
## Contrainte : [Nom] — de [Source]
> [La contrainte, une phrase]

### Idées

1. **[Pitch en une ligne]**
   [2-3 phrases — ce qui est fait concrètement, pourquoi c'est intéressant]
   ⏱ [weekend/semaine/mois]  •  🔧 [stack/medium/matériaux]
   ↳ Mode d'échec honnête : [...]

2. ...
```

Pour les autres méthodes, utiliser le format que la méthode spécifie (TRIZ → analyse de contradiction ; OuLiPo → texte contraint ; Stratégies obliques → une carte appliquée → prochain mouvement). Ne pas forcer toutes les méthodes dans le template de contrainte.

**Pour chaque set d'idées, quelle que soit la méthode :**
- Nommer la méthode utilisée. Sur terrain slop, nommer les idées évidentes refusées.
- Donner à chaque idée son mécanisme concret et son mode d'échec honnête.
- Marquer au moins une idée comme **ancrée** (🔩) — réalisable maintenant, non-évidente avec une vraie première étape.

---

---

## Méthodes locales — frameworks de résolution de problèmes

> Trois lentilles à passer en priorité sur tout problème de *résolution* (génération de solutions,
> pas argumentation). **Réflexe d'enchaînement :** Premiers principes (descendre au fond, ne pas
> résoudre un faux problème hérité d'une exigence non questionnée) → Transfert analogique (cette
> forme est-elle déjà résolue ailleurs, et le verrou d'hier vient-il de sauter ?) → Substitution
> d'entités (faire varier chaque pièce, en continu, pour générer ET stress-tester ce qui est
> critique). Source : guide de l'utilisateur, 2026-06-26. Règle qui les relie : ne jamais accepter la config
> actuelle comme donnée — chaque pièce/exigence/frontière est candidate au remplacement tant qu'on
> n'a pas prouvé qu'elle est porteuse.

### Premiers principes — version opérationnelle (Musk, doc. Isaacson)
Complète l'entrée stub de la table (« ARTEFACT — hypothèses accumulées à questionner »).
- **Idiot Index** = coût du composant ÷ coût de ses matières premières. Ratio élevé = design ou
  procédé massivement améliorable ; fixe le plancher de coût. Commence toujours par le calculer sur
  le poste cher.
- **Algorithme en 5 étapes, ordre STRICT** : 1) **Questionner** chaque exigence — et l'attacher au
  nom de qui l'a posée (les exigences de gens intelligents sont les plus dangereuses, car les moins
  questionnées). 2) **Supprimer** toute pièce/process qu'on peut (si tu ne réintroduis pas ≥10 %
  ensuite, tu n'as pas assez coupé). 3) **Simplifier** — seulement *après* avoir supprimé. 4)
  **Accélérer** le cycle. 5) **Automatiser** — en dernier. **Erreur n°1 : optimiser/automatiser
  (3-5) une étape qu'on aurait dû supprimer (2).**
- **Test de fin** : « si on repartait de zéro aujourd'hui, avec les seules contraintes réelles,
  construirait-on *ça* ? » L'écart existant↔reconstruit = la zone de solution.

### Substitution d'entités (génératif + diagnostic)
Étend le **S de SCAMPER** (substitute) avec un **mode diagnostic** que SCAMPER n'a pas.
- **Génératif** : remplace une pièce (composant, acteur, matériau, contrainte, étape) par un
  substitut moins cher / plus disponible / déjà maîtrisé / venu d'un autre domaine → des options
  invisibles tant qu'on reste collé à la config actuelle.
- **Diagnostic (l'ajout)** : substitue pour *tester ce qui est porteur*. Remplacer ne casse rien →
  la pièce n'était pas essentielle. Tout s'effondre → tu as trouvé le point critique. Sert à
  **stress-tester** un système et à dé-risquer *avant* de s'engager.
- Structure : 1) cartographie les entités (qui/quoi fait quoi, avec quoi, sous quelle contrainte) ;
  2) pour chacune « et si on la remplaçait par ___ ? » ; 3) observe l'aval (coûts, dépendances,
  ruptures). **Piège** : le substitut doit pouvoir tenir le rôle (honnêteté fonctionnelle) — le mode
  diagnostic protège en testant la rupture avant l'engagement.

### Transfert analogique — l'invariant
Plus rigoureux que « Analogie et blending » de la table : extraire l'**invariant structurel** (le
squelette logique/mathématique débarrassé de l'habillage métier), trouver un domaine où il est déjà
résolu, puis vérifier que le **verrou** d'hier vient de sauter chez toi (coût du compute, densité de
capteurs, donnée dispo). Méthode : décris le problème *sans son vocabulaire métier* → « où ce
squelette est-il déjà résolu ? » → « ce qui le rendait coûteux là-bas a-t-il sauté ici ? ». **Piège :
invariant *formel*, pas analogie de surface** (« c'est un peu comme… » ne sert à rien).

---

## Méthode locale — Arbitrage d'autorité latente

> **Cas particulier** de **Substitution d'entités** (on substitue la *source d'autorité*) + **Premiers
> principes** (on *supprime* l'exigence « inventer une certification ») appliqués à un problème de
> confiance. Généralisation au domaine confiance de l'*Ideal Final Result* de Genrich Altshuller
> (TRIZ) : « la meilleure solution remplit la fonction avec des ressources **déjà présentes dans le
> système**, à coût nul ». Inventée le 2026-06-26 (utilisateur + agent).

**Déclencheur :** tu es sur le point d'**inventer** un signal de confiance — un label, une
certification, un organisme, une autorité, un badge « validé par nous ».

**Le mouvement :** STOP. Une autorité a presque toujours *déjà tranché* la question — mais sa
décision est **illisible** pour ceux qui en auraient besoin (langue, jargon, format, accès). Tu ne
fabriques pas l'autorité (mensonge, fragile, illégal), tu deviens son **interface lisible**.
L'écart entre un mandat existant-mais-opaque et l'audience qui ne sait pas le lire = **le produit**.

**Les 3 questions de la méthode :**
1. Quelle institution (État, ordre, registre public) **certifie déjà légalement** ce que je veux certifier ?
2. Pour **qui** cette certification est-elle illisible — et pourquoi (langue ? jargon ? accès ? format) ?
3. Quelle **donnée publique** la matérialise, et puis-je la **republier traduite / contextualisée** ?

**Sortie :** un produit qui **capte la valeur-confiance sans manufacturer la confiance**.

**Mode d'échec (la seule règle dure) :** ne jamais promettre **plus** que ce que le mandat
sous-jacent garantit réellement. Sinon tu refabriques le mensonge que la méthode sert à éviter.
La méthode n'autorise QUE de **relayer** ce qui est déjà garanti, daté et vérifiable.

**Exemples (l'autorité existe déjà, mais opaque pour le bénéficiaire) :**
carte G / garantie financière loi Hoguet (agences immo, fichier CCI public) · Orias (courtiers) ·
DPE (immobilier) · Nutri-score · label AB (bio) · avis de situation SIRENE · barreau (« cet avocat
est-il réel ? »). À chaque fois : republier + traduire + contextualiser une décision officielle illisible.

**Cas d'origine :** annuaire « certification » pour agences immobilières — au lieu
d'inventer un organisme (piège juridique : pratique trompeuse), surfacer la **carte G + garantie
financière + SIREN** déjà publiques, traduites pour étudiants étrangers.

## Liens
- [[anti-slop]] — règles anti-slop à appliquer à toute génération d'idées
- [[arbitrage-autorite-latente]] · [[annuaire-certification-carte-g]] — application veille
