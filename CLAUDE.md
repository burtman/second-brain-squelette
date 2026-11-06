# Second Brain — Contrat de fonctionnement

Ce vault Obsidian est mon **cerveau externe**. Il combine deux systèmes distincts :
1. **LLM Wiki** (pattern Karpathy) — connaissance compilée et reliée, maintenue par l'agent IA.
2. **PKM / PARA** — capture quotidienne, projets, domaines, to-do.

Tu es l'agent IA qui maintient ce vault, quel que soit le modèle (Claude, GPT, Grok…). Respecte les règles ci-dessous.
Ce fichier est lu sous deux noms : `CLAUDE.md` (Claude Code) et `AGENTS.md` (Codex/GPT, OpenCode), qui est un lien
vers lui. On ne modifie que `CLAUDE.md`.

---

## Structure des dossiers

| Dossier | Rôle | Qui écrit |
|---|---|---|
| `00-inbox/` | **Le système de tâches** : `_index.md` = la liste cochable, une **fiche par tâche** (`AAAA-MM-JJ-slug.md`, la date = l'échéance) + capture rapide au vol | Moi + toi |
| `01-daily/` | Journal du jour (`YYYY-MM-DD.md`) : notes, calls, décisions. **Pas de to-do** — elles vivent dans `00-inbox/` | Moi (+ toi sur demande) |
| `02-projects/` | Projets actifs : un objectif + une échéance. Un fichier `<projet>-context.md` par projet | Moi + toi |
| `03-areas/` | Domaines permanents (santé, business, finance, perso…) + `veille/` | Moi + toi |
| `raw/` | **Sources brutes** : articles, PDF, transcripts. SOURCE DE VÉRITÉ. | Moi (dépôt) |
| `wiki/` | Pages de connaissance structurées et reliées | **Toi** |
| `skills/` | Skills opérationnelles (règles de comportement pour l'agent) | Toi sur demande |
| `99-archive/` | Projets clos / notes obsolètes | Toi sur demande |

---

## Règles pour toi (l'agent)

### Lecture / contexte (ordre, pour économiser les tokens)

**Pour un travail sur un projet actif :**
1. Lis `02-projects/<projet>-context.md` → il liste les seules pages wiki autorisées.
2. Lis uniquement les pages listées dans ce fichier.
3. Si une autre page semble nécessaire, le signaler avant de la lire.

**Pour une question transversale ou une ingestion :**
1. Lis `wiki/hot.md` (pointeurs projets + décisions clés, max 25 lignes).
2. Si besoin de plus, lis `wiki/index.md`.
3. Seulement ensuite, ouvre les pages individuelles concernées.

**Règle absolue : ne jamais scanner le vault entier. Lire à la demande, pas par anticipation.**

### Poids des imports (RÈGLE)
- **Aucun fichier de plus de 1 Mo n'entre dans le vault sans mon accord explicite ou ma demande.**
  Vérifie la taille **avant** de déposer quoi que ce soit ; au-delà du seuil, demande — même si le
  dépôt découle d'une tâche que je t'ai confiée.
- **Raison** : le vault est un dépôt Git. Un binaire committé y reste pour toujours (le retirer impose
  une réécriture d'historique qui casse tous les clones), et il gonfle chaque clone à perpétuité.
- **Ce qui entre à la place** : la **transcription** du document en Markdown, avec le nom du fichier
  d'origine et sa provenance (identifiant et date du mail, URL, etc.). L'original reste à sa source —
  boîte mail, Drive, disque — qui redevient la source de vérité. On ne supprime **jamais** la source.
- Vaut pour toute pièce jointe, export, PDF, image, archive. En cas de doute sur la taille : mesure.

### Frontière raw → wiki (RÈGLE CARDINALE)
- Tu **ne réécris JAMAIS** les fichiers de `raw/`. Tu les lis.
- Quand j'ajoute une source dans `raw/` et te demande de l'« ingérer » :
  - Crée/enrichis des pages dans `wiki/` (concepts, entités, sources).
  - **Relie** chaque nouvelle page aux pages existantes via `[[liens wikilink]]`.
  - Mets à jour `wiki/index.md` et `wiki/hot.md`.

### Ne pas mélanger connaissance et tâches
- Les tâches vont dans `00-inbox/`, les notes du jour dans `01-daily/`, **jamais** dans `wiki/`.
- `wiki/` ne contient que de la connaissance durable et reliée.

### Système de tâches `00-inbox/` (RÈGLE)
- **Trois façons de clore une fiche** : **Fait** (`done`) · **Répondu, pas exécuté** (`answered`) · **Annulé** (`killed`).
  Chaque fiche porte les trois cases + une zone commentaire libre, lue avant tout le reste.
  Une fiche `answered` **ne part au bin qu'accompagnée d'une fiche successeur** portant le travail restant.
- **Une tâche = une fiche = un fichier.** Gabarit : `00-inbox/_template-fiche.md`. Nom : `AAAA-MM-JJ-slug.md`
  où la date est l'**échéance** → le dossier se trie par urgence. Échéance qui bouge = fichier renommé + `reports` +1.
- Chaque fiche porte : `created`, `due`, `owner`, `witness`, `reports`, un **livrable binaire**, un **Fil** de discussion
  (l'utilisateur et l'agent écrivent dedans, daté et signé du nom du modèle : Claude, GPT, Grok…) et une section **Sortie**.
- **Fin de vie = archivage dans `00-inbox/bin/AAAA-MM/`, traité exactement comme une suppression.**
  Interdiction d'archiver une fiche avant d'avoir (1) écrit la trace prévue dans `Sortie` (jalon coché dans
  `roadmap.md`, page `wiki/` ou `<projet>-context.md` mise à jour, `hot.md` si structurant), (2) **committé**.
  Le nom du fichier ne change pas à l'archivage (les wikilinks continuent de résoudre) ; `closed:` et `propage:`
  sont renseignés dans le frontmatter. Règles complètes : `00-inbox/bin/_regles.md`.
- **État intermédiaire obligatoire** : une fiche cochée « Fait » dont la `Sortie` a encore une case vide **reste
  dans `00-inbox/`** et apparaît en « dette de propagation » dans `_index.md`. Le bin n'est pas une sortie de secours.
- **Invariant vérifiable** : une fiche dans `bin/` ne contient **aucune case vide**.
  Contrôle : `grep -rln '^- \[ \]' 00-inbox/bin/` doit ne rien retourner. À lancer à chaque revue.
- Une fiche `killed` s'archive comme une `done`, avec `raison:`, et propage **davantage** : « on a décidé de ne pas
  faire X, parce que Y » est l'information la plus vite reperdue et celle qui évite de reposer la question.
- **Ne jamais lire `00-inbox/bin/` par anticipation** (règle d'économie de contexte). Sur demande explicite seulement.
- `_index.md` est un **miroir** de l'état des fiches. En cas de divergence, **la fiche gagne**.
- Pas de fiche sans échéance : une tâche sans date reste une ligne brute dans la section « à tuer ou à dater » de l'index.
- Au **3ᵉ report** d'une fiche : tuer, déléguer ou découper. Pas de 4ᵉ report.
- Aucune tâche n'est créée avec un `owner`/`witness` qui n'a pas été prévenu.

### Frontmatter obligatoire sur toute note que tu crées
```yaml
---
type: concept | entity | source | project | area | daily
status: draft | active | done | archived
date: YYYY-MM-DD
tags: []
---
```

### Style
- Markdown brut, pas de dépendance à un plugin pour que le contenu reste lisible.
- Notes atomiques : une idée = une page, reliée aux autres.
- Réponds-moi en français.

---

## Workflow type
- « ingère ça » / « ingest raw/xxx » / « range ça dans la veille » → **applique la skill `skills/veille-ingestion/`** :
  dépôt brut fidèle + filtre slop + fiche d'analyse (résumé / insights / accords / désaccords / application projet) + reliure.
- « qu'est-ce que je sais sur X ? » → réponds en t'appuyant sur le wiki, cite les `[[pages]]`.
- « note du jour » → crée/ouvre `01-daily/YYYY-MM-DD.md`.
- « lint the wiki » → détecte orphelins, liens morts, contradictions, doublons.
- **Revue mensuelle** (le 1er du mois) : orphelins, doublons de tags, projets clos → `99-archive/`, mise à jour de ce `CLAUDE.md`.

---

## Skills actives en permanence

Les fichiers dans `skills/` définissent des comportements que tu dois appliquer systématiquement, pas seulement quand demandé explicitement.

**`skills/anti-slop.md` — TOUJOURS actif :**
- Refuser les 3 premières idées générées (les plus évidentes) avant de proposer quoi que ce soit
- Sur terrain slop (startup/IA/productivité) : refuser les 5 premières
- Spécificité > abstraction : mécanismes concrets, pas de verbes vagues
- Chaque idée = mécanisme + mode d'échec honnête

**`skills/veille-ingestion/` — actif à toute ingestion de source :**
- Dépôt brut fidèle dans `raw/` (jamais réécrit) + `SOURCES.md` listant aussi les contenus exclus (slop)
- Fiche de veille avec les 5 sections d'analyse imposées + reliure wikilinks bidirectionnelle + index
- Definition of Done à cocher avant de rendre

**`skills/audit-seo-geo/` — actif à toute demande d'audit SEO, GEO ou de visibilité dans les IA :**
- 8 étapes chargées une par une, une preuve (URL + méthode) derrière chaque constat, toute absence vérifiée deux fois
- Trois modes : complet, flash de prospection, re-audit à 30/60/90 jours ; livrables dans `audit-livrables/<client>/`

**`skills/creative-ideation.md` — actif quand l'utilisateur demande des idées :**
- Router par phase et domaine avant de générer
- Nommer la méthode utilisée
- Inclure au moins une idée réalisable maintenant

---

## Démarrage minimal
Pas de plugins ni de MCP pour l'instant. On ajoute uniquement quand un vrai besoin apparaît.
