---
type: skill
status: active
date: 2026-06-25
tags: [skill, qualité, idéation, règles-universelles]
source: https://github.com/NousResearch/hermes-agent/blob/main/optional-skills/creative/creative-ideation/SKILL.md
---

# Anti-Slop — Règles universelles de qualité idéative

Règles à appliquer à **toute** génération d'idées, quelle que soit la tâche. Ces règles s'appliquent en permanence — pas seulement pour le brainstorming créatif.

## Les 5 règles

**1. Refuser les 3 premières idées**
Les 3 premières idées qui viennent sont les plus attendues, les plus génériques, les plus "centrées-LLM". Générer → identifier les évidentes → les jeter → recommencer avec ce qui reste.

Sur **terrain à fort slop** (idées de startup, apps IA/productivité/bien-être/voyage/fitness) : refuser les **5** premières.

**2. Spécificité > abstraction**
- Slop : "une app pour connecter les gens", "un outil de suivi d'habitudes"
- Bien : "un script Python de 300 lignes qui scrape X et envoie un SMS quand Y dépasse Z"

Nommer une techno n'est pas de la spécificité. Nommer le mécanisme, oui.

**3. Contrainte + direction**
Sans contrainte = pas de traction. Sans direction = pas de forme. Une idée sans contrainte ni direction est toujours du slop.

**4. Le bizarre doit aussi être bon**
Frame-breaking est l'objectif, mais une idée étrange sans mécanisme réel ou raison d'exister est son propre mode d'échec. Chaque set doit inclure au moins une idée **réalisable maintenant** — non-évidente mais concrète, avec une première étape réelle.

**5. Profondeur par idée, pas décoration**
Pour chaque idée : mécanisme concret + mode d'échec honnête / trade-off / pour qui. Cette profondeur est ce qui fait atterrir une idée. Ne pas couper.

## Check avant toute génération

- [ ] Les premières idées qui me viennent sont les évidentes → les jeter
- [ ] L'output ressemble à une liste générique numérotée → choisir une méthode d'abord
- [ ] Les idées utilisent des verbes vagues ("connecter", "optimiser", "améliorer") → descendre au niveau mécanisme
- [ ] Vais écrire "Voici 5 idées :" → STOP. Choisir une méthode, router, puis générer.

## Liens
- [[creative-ideation]] — skill complète avec méthodes de routage par phase et domaine
