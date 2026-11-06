---
type: concept
status: active
date: 2026-11-06
tags: [skill, seo, geo, audit, prospection]
---

# Les modes courts

Les deux modes appliquent `regles.md` en entier. Plus court ne veut pas dire moins prouvé.

## Flash · prospection (15 à 20 minutes)

**Pour** ouvrir une conversation avec un prospect. Une page, trois constats prouvés, trois opportunités. Ce n'est
pas l'audit : c'est ce qu'on voit de l'extérieur, et ça le dit.

**Cadrage** (3 questions) : URL, type d'activité, au nom de qui on signe (votre agence, une autre marque, ou personne).

**Relevé** (environ 7 min), 12 contrôles au plus, chacun avec son statut :
- title, meta description, H1 de l'accueil, avec leur longueur ;
- un paragraphe-réponse de 40 à 60 mots sous le bandeau, oui ou non ;
- codes HTTP de robots.txt, sitemap.xml, llms.txt ;
- robots de recherche IA autorisés ou bloqués dans robots.txt ;
- JSON-LD sur l'accueil, et ses types ;
- ordre de grandeur `site:domaine` ;
- réseaux liés dans le pied de page. Ce qui n'y est pas est `Non vérifié`, jamais absent : le protocole complet
  n'est pas fait en mode flash.

**IA** (environ 8 min) : 5 questions (2 de marque, 3 de catégorie), posées à Google sur google.fr et à Claude.
ChatGPT, Perplexity et Gemini ne sont pas testés : le dire, c'est un argument pour l'audit complet.
Un score indicatif sur 100, annoncé comme une estimation de surface, et 1 ou 2 concurrents vus dans les réponses.

**La page** (environ 5 min) :
1. « Diagnostic flash SEO et visibilité IA · <site> · <date> » ;
2. le score indicatif, avec la mention « estimation de surface » ;
3. trois constats, chacun avec sa preuve (code HTTP, question testée), formulés comme des occasions et jamais
   comme des reproches ;
4. trois opportunités : ce que le prospect gagne, sans le mode d'emploi complet ;
5. une ligne de méthode : ce que l'audit complet ajoute (tests en direct dans ChatGPT, Perplexity et Gemini,
   concurrents, plan prêt à coller) ;
6. le contact.

**Fichiers** : `audit-livrables/<slug>/flash.md` (la page), `flash-notes.md` (les contrôles bruts, pour préparer
l'appel, jamais envoyés), et le PDF d'une page, mesuré avant tout commit.

## Re-audit (30, 60 ou 90 jours après un complet)

**Pour** mesurer ce qui a bougé. Demande le dossier `audit-livrables/<slug>/` de l'audit initial ; sans lui, pas
de re-audit, on propose un audit complet.

1. **État initial** : relire les notes, le score IA, les failles, la feuille de route et `grille-ia.md`.
   Rien de ce qui manque n'est reconstruit de mémoire : une dimension sans donnée de départ est « non comparable ».
2. **Deux questions au client** : quelles actions ont été faites ? qu'est-ce qui a changé d'autre (refonte, presse,
   nouveaux contenus) ? Ses réponses sont `Déduit` tant qu'on ne les a pas constatées.
3. **Retests**, dans cet ordre :
   - chaque preuve de faille du Diagnostic, rejouée (même URL, même commande) : corrigée, en partie, inchangée ;
   - les fichiers de l'étape 3 ;
   - l'étape 7 avec **les mêmes questions et le même niveau** de test. Si le niveau change (Claude in Chrome
     disponible entre-temps), l'écrire en tête : la comparaison n'est plus à périmètre constant ;
   - les dimensions touchées par les changements. Les autres gardent leur note, marquée « non retestée ».
4. **Le document de suivi** : avant et après pour la note globale, le score IA, la part de voix, la tonalité et le
   nombre de failles corrigées ; ce qui a probablement payé ; ce qui reste ; les 5 prochaines actions.

**Corrélation, pas causalité** : « le score a gagné 12 points ; dans la période, les actions X et Y ont été faites ;
le lien est probable, pas prouvé ». Les IA changent aussi leurs sources d'elles-mêmes.

**Fichier** : `audit-livrables/<slug>/reaudit-J<30|60|90>.md`, qui sert de référence au re-audit suivant.
