# Second brain : squelette d'un vault Obsidian piloté par un agent IA

Version épurée (structure, règles, skills, aucune donnée) d'un vault utilisé au quotidien depuis mi-2026.
Il applique le pattern **LLM Wiki** d'Andrej Karpathy et y ajoute ce que l'usage a rendu nécessaire.

## L'idée en trois phrases

- **Obsidian est l'IDE, l'agent est le programmeur, le wiki est le code.** L'humain dépose des sources brutes
  dans `raw/`, l'agent compile une connaissance reliée dans `wiki/`, et ne touche jamais à `raw/`.
- **Le contrat est un fichier texte** : `CLAUDE.md` (aussi lu sous le nom `AGENTS.md`). Tout agent qui ouvre le
  dossier, quel que soit le modèle, hérite des mêmes règles.
- **Lire à la demande, jamais scanner.** `wiki/hot.md` (25 lignes) puis `wiki/index.md` puis la page utile.
  C'est ce qui garde le coût en tokens stable quand le vault grossit.

## Ce que ce squelette ajoute au pattern de Karpathy

1. **Un système de tâches en fiches** (`00-inbox/`) : une tâche = un fichier daté à l'échéance, trois façons de clore
   (fait, répondu sans exécuter, annulé), et une section « Sortie » à solder avant archivage. Une tâche ne disparaît
   jamais sans avoir déposé sa connaissance quelque part. Règles dans `00-inbox/bin/_regles.md`.
2. **Un budget de lecture par projet** : `02-projects/<projet>-context.md` liste les seules pages wiki que l'agent a
   le droit de lire pour ce projet.
3. **Des skills actives en permanence** (`skills/`) : anti-slop (refuser les premières idées, mécanisme + mode
   d'échec), ingestion de veille (filtre slop, 5 sections d'analyse, reliure), idéation créative, et un
   **audit SEO + GEO** complet (`skills/audit-seo-geo/`) qui mesure aussi la visibilité d'une marque dans les IA.
4. **Une règle de poids** : rien au-dessus de 1 Mo dans le dépôt Git, on dépose la transcription Markdown et
   l'original reste à sa source.

## Démarrer en dix minutes

1. Installer [Obsidian](https://obsidian.md) et [Claude Code](https://claude.com/claude-code) (ou Codex, OpenCode,
   n'importe quel agent qui lit `AGENTS.md`).
2. Cloner ce dépôt, l'ouvrir comme coffre dans Obsidian.
3. Dans Obsidian : Paramètres → Fichiers et liens → Fichiers exclus → ajouter `00-inbox/bin`.
4. Ouvrir un terminal dans le dossier, lancer l'agent, et commencer par :
   « Lis CLAUDE.md. Voici une première source dans raw/, ingère-la. »
5. Adapter `CLAUDE.md` à mesure : chaque règle du fichier existe parce qu'un problème concret l'a imposée.
   Supprimer celles qui ne servent pas, ajouter les vôtres au fil des accidents.

## Structure

| Dossier | Rôle | Qui écrit |
|---|---|---|
| `00-inbox/` | tâches (une fiche par tâche) + capture rapide | humain + agent |
| `01-daily/` | journal du jour, sans to-do | humain |
| `02-projects/` | projets actifs, un `<projet>-context.md` chacun, `roadmap.md` | humain + agent |
| `03-areas/` | domaines permanents, dont `veille/` | humain + agent |
| `raw/` | sources brutes, source de vérité, jamais réécrites | humain |
| `wiki/` | connaissance compilée et reliée (`hot.md`, `index.md`, pages) | agent |
| `skills/` | règles de comportement de l'agent | agent sur demande |
| `audit-livrables/` | dossiers d'audit SEO + GEO, un par client (créé au premier audit) | agent |
| `99-archive/` | projets clos | agent sur demande |

## Références

- Andrej Karpathy, « LLM Wiki » (le gist d'origine) : https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
- Nate Herk, vidéo pas à pas Obsidian + Claude Code : https://www.youtube.com/watch?v=sboNwYmH3AY
- Guide complet « Build an AI Second Brain with Claude + Obsidian » : https://www.youtube.com/watch?v=HuREI6lks4s
- Article en français (Angelo Lima) : https://angelo-lima.fr/en/karpathy-second-brain-obsidian-claude-en/
- Skill anti-slop : adaptée de Nous Research, `hermes-agent/optional-skills/creative/creative-ideation`

## Licence

MIT. Prenez, adaptez, cassez.
