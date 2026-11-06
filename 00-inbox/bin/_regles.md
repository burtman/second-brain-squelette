---
type: meta
status: active
date: 2026-07-30
tags: [pilotage, archive]
---

# bin/ — fiches closes

> **Règle cardinale : entrer dans `bin/` équivaut à être supprimée.** Le bin est un filet de sécurité pour
> *relire* une tâche passée, jamais une excuse pour reporter la propagation. Une fiche qui arrive ici a déjà
> livré tout ce qu'elle avait de durable au wiki, au projet ou à la roadmap.

## Le cycle de vie d'une fiche

| État | Où vit la fiche | Ce qui reste à faire |
|---|---|---|
| `open` | `00-inbox/` | la faire |
| `blocked` | `00-inbox/` | attendre une réponse (l'index dit qui) |
| `done` / `answered` / `killed` | **encore `00-inbox/`** | ⚠️ **propager** — la fiche reste visible et gênante tant que `Sortie` n'est pas soldée |
| archivée | `00-inbox/bin/AAAA-MM/` | rien. Fiche closue, propagation faite, commit fait |

**Trois manières de clore, depuis le 11/08/2026** (cf. `_template-fiche.md`) : `done` = le livrable existe ·
`answered` = l'utilisateur a tranché mais le travail reste à faire → **une fiche successeur est obligatoire**, son nom
va dans `propage:`, sinon la fiche ne part pas au bin · `killed` = on ne le fera pas, `raison:` obligatoire.
La distinction n'est pas cosmétique : `answered` sans successeur, c'est exactement le mécanisme qui fait
survivre une décision prise sans le travail qui va avec : la décision est actée, le travail disparaît avec la fiche.

**Cocher « Fait » ne déplace rien.** C'est la `Sortie` entièrement cochée qui autorise le passage au bin.
L'état intermédiaire `done`-mais-pas-propagé est **volontairement inconfortable** : c'est lui qui garantit
que la connaissance sort de la tâche avant que la tâche disparaisse de la vue.

## Invariant vérifiable

> **Une fiche dans `bin/` ne doit contenir aucune case vide.**

La case d'état retenue est cochée — **les deux options non retenues sont supprimées à la clôture**, pas
laissées vides — et toutes les lignes de `Sortie` sont cochées aussi. Donc :

```bash
grep -rln '^- \[ \]' 00-inbox/bin/    # doit ne rien retourner
```

Si cette commande retourne un fichier, il y a une **dette de propagation** : la fiche est sortie de la vue
sans avoir livré son contenu. Je la ressors du bin et je la traite. Ce contrôle passe à chaque revue.

## Règles de rangement

- **Sous-dossiers par mois de clôture** : `bin/2026-07/`, `bin/2026-08/`… Le bin reste navigable à 200 fiches.
- **Le nom du fichier ne change pas** à l'archivage. Il garde sa date d'échéance. Deux raisons : les wikilinks
  des autres notes continuent de résoudre (Obsidian retrouve un fichier par son nom, quel que soit le dossier),
  et l'historique git ne subit qu'un seul déplacement au lieu d'un renommage + un déplacement.
- **La date de clôture va dans le frontmatter** (`closed:`), pas dans le nom.
- **Une fiche `killed` s'archive comme une fiche `done`**, avec un champ `raison:`. Et elle propage *davantage* :
  « on a décidé de ne pas faire X, parce que Y » est une information plus rare et plus utile qu'une tâche réussie —
  c'est celle qu'on reperd le plus vite, et celle qui évite de reposer la question dans trois mois.

## Pour l'agent

- **Ne jamais lire `bin/` par anticipation** (règle d'économie de contexte de `CLAUDE.md`). On l'ouvre sur demande
  explicite, ou pour enquêter sur une tâche passée précise.
- À exclure de la recherche Obsidian : Paramètres → Fichiers et liens → Fichiers exclus → `00-inbox/bin`.
  Sinon chaque recherche remonte l'archive et le bruit augmente avec le temps.
- **Committer avant de déplacer.** Une fiche déplacée sans commit préalable ne laisse aucune trace de son fil
  de discussion dans l'historique si le bin est purgé plus tard.
