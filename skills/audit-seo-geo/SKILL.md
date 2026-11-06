---
name: audit-seo-geo
description: Auditer un site pour Google et pour les IA (ChatGPT, Perplexity, Gemini, Claude, AI Overviews) avec une preuve derrière chaque constat, puis livrer un Diagnostic et un Plan d'exécution prêt à coller. Utiliser dès qu'on demande un audit SEO, un audit GEO, la visibilité d'une marque dans les réponses des IA, un diagnostic flash pour prospecter, ou un re-audit à 30, 60 ou 90 jours.
type: concept
status: active
date: 2026-11-06
tags: [skill, seo, geo, audit, prospection]
---

# Audit SEO + GEO

Une méthode d'audit en 8 étapes, pensée pour un agent qui a un terminal, un navigateur et des sous-agents
(Claude Code ou équivalent). Elle s'inspire des idées de la Roso SEO Squad (RosoAI), réécrites et resserrées :
chaque constat porte sa preuve, et toute affirmation d'absence est vérifiée deux fois.

## Ce que ça produit

Un dossier `audit-livrables/<slug-client>/` qui contient :
- `fiche-site.md` : le relevé du site, base commune à toutes les étapes ;
- un compte rendu par étape (`1-releve.md` … `7-visibilite-ia.md`), chacun avec ses preuves ;
- `etat.json` : où en est l'audit, pour reprendre après une coupure ;
- deux documents pour le client : le **Diagnostic** (ce qui va, ce qui bloque, pourquoi) et le **Plan d'exécution**
  (quoi faire, avec le code et les textes prêts à coller, et comment vérifier).

## Trois modes

| Mode | Pour quoi | Durée | Où |
|---|---|---|---|
| **Complet** | audit client, ou votre propre site | 2 à 4 h | étapes 1 à 8 ci-dessous |
| **Flash** | prospection : une page qui ouvre la conversation | 15 à 20 min | `modes.md`, section Flash |
| **Re-audit** | 30, 60 ou 90 jours après un audit complet | 30 à 60 min | `modes.md`, section Re-audit |

## Démarrage (dans cet ordre)

1. Lire `regles.md` en entier. Il s'applique à toutes les étapes et à tous les modes.
2. Poser les questions de cadrage, en un seul message, sans en ajouter :
   - URL du site et nom de la marque ;
   - type d'activité (la liste est dans `etapes/1-releve.md`) ;
   - concurrents connus, avec leur URL (2 à 5) ;
   - accès : Search Console du site ouverte dans le navigateur de l'utilisateur ? Navigateur piloté par l'agent (sessions
     ChatGPT, Perplexity, Gemini connectées) ?
   - pour qui sont les livrables (client, prospect, nous) et le registre : tutoiement ou vouvoiement ;
   - niveau de test dans les IA : **live complet**, **live ciblé** (recommandé) ou **sans live** (voir étape 7) ;
   - rythme : pause après chaque étape pour valider, ou tout d'une traite.
3. Créer `audit-livrables/<slug>/etat.json` depuis `modeles/etat.json`, rempli avec les réponses.

## Déroulé

Charger le fichier d'une étape **au moment de la lancer**, jamais avant. Le compte rendu d'une étape validée fait
foi ensuite : on le relit, on ne s'appuie pas sur sa mémoire.

| # | Étape | Fichier | A besoin de | Exécution |
|---|---|---|---|---|
| 1 | Relevé du site | `etapes/1-releve.md` | cadrage | moi |
| 2 | Offre et page d'accueil | `etapes/2-offre-accueil.md` | 1 | moi |
| 3 | Technique et accès des robots IA | `etapes/3-technique.md` | 1 | sous-agent, puis moi |
| 4 | Requêtes et concurrents | `etapes/4-requetes-concurrents.md` | 1, 2 | sous-agent, puis moi |
| 5 | Autorité, entité, réputation | `etapes/5-autorite.md` | 1 | sous-agent, puis moi |
| 6 | Contenu citable | `etapes/6-contenu.md` | 2, 4 | moi |
| 7 | Visibilité dans les IA | `etapes/7-visibilite-ia.md` | 4, 5 | mixte |
| 8 | Cohérence, notes, livrables | `etapes/8-synthese.md` | toutes | moi |

**Parallélisme.** Après l'étape 2, les étapes 3, 4 et 5 partent en même temps, chacune dans un sous-agent
sur un modèle plus léger (Sonnet par exemple) qui reçoit le fichier de son étape, `regles.md` et `fiche-site.md`. Le sous-agent collecte et
rapporte des preuves brutes (URL, code HTTP, extrait, commande). C'est moi qui juge, note et écris le compte rendu :
la collecte sur un modèle léger, l'analyse sur le modèle principal. Annoncer la durée avant de lancer le parallèle.

**Rythme « pause ».** Après chaque compte rendu : montrer l'essentiel en 3 lignes et la note, demander
« on continue ? ». **Rythme « d'une traite »** : enchaîner, sauf pour le test live dans les IA, qui consomme
du quota et n'est jamais lancé sans le niveau choisi au cadrage.

## Reprise après coupure

« On reprend l'audit de X » : lire `audit-livrables/<slug>/etat.json`. Une étape `validee` ne se refait pas, son
compte rendu fait foi. Une étape commencée sans compte rendu écrit repart de zéro. Annoncer en 2 lignes ce qui
est fait et où on reprend.

## Ce que la skill ne fait pas

- Pas de suivi continu : c'est un audit à une date. Le suivi passe par le re-audit.
- Pas d'analyse de liens entrants : il faudrait un outil payant (Ahrefs, Semrush) qu'on n'a pas.
- Pas de volume de recherche sans source nommée.
- Pas de crawl complet : on lit un échantillon et on dit lequel.
- Pas de rédaction d'articles pendant l'audit. Ça se fait après, sur demande, à partir du plan éditorial.
