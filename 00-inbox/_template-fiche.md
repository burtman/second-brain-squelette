---
type: task
status: open
created: 2026-07-30
due: 2026-07-30
closed:
owner: moi
witness: qui/quoi constate que c'est fait
reports: 0
sortie: à définir
propage:
raison:
tags: []
---

# <Verbe + objet, une phrase courte>

## Où en est cette fiche — coche **une** case, commente en dessous

- [ ] **Fait** — le livrable existe, on peut le montrer
- [ ] **Répondu, pas exécuté** — tu as tranché, le travail reste à faire (par toi ou par quelqu'un d'autre)
- [ ] **Annulé** — on ne le fera pas. Écris pourquoi : c'est l'information qui se reperd le plus vite

> 💬 **Commentaire** — écris ici, une ligne suffit. C'est ce que je lis en premier, avant tout le reste.

## 📌 Instructions de l'utilisateur

> Écris ici ce que tu veux que je fasse. Style libre, pas de format à respecter, une phrase suffit.
> Je lis cette zone **avant** tout le reste de la fiche, et je fais ce qu'elle dit — même si ça contredit
> ce que j'avais écrit dans le Fil. Exemples : « mets ça en pause », « tue cette fiche », « décale à vendredi »,
> « c'est fait mais vérifie X », « creuse ce point avant de cocher ».
> Si l'instruction contredit une règle du vault, je l'exécute **et** je consigne l'objection dans le Fil.
> Si elle est ambiguë, je ne devine pas : je demande.

**Livrable binaire** : ce qu'on peut montrer. Pas « avancer sur », pas « réfléchir à ».

## Fil

- **JJ/MM · agent** — pourquoi cette tâche existe, ce qui est déjà prêt, ce qui bloque.
- **JJ/MM · moi** — ta réponse. Écris directement ici, je lis.

## Sortie — à solder avant l'archivage

> Où va la trace. **Tant qu'une case ci-dessous est vide, la fiche reste dans `00-inbox/`**, même cochée « Fait ».
> Passer au bin sans solder cette section = perdre l'info exactement comme si on avait supprimé la fiche.

- [ ] Jalon correspondant coché dans `02-projects/roadmap.md`
- [ ] Connaissance durable écrite dans : `wiki/...` ou `02-projects/<projet>-context.md` — ou **« rien à propager »**, écrit explicitement
- [ ] `hot.md` / `index.md` mis à jour si c'est une décision structurante

---
**Les trois états, et ce qu'ils déclenchent** *(ajoutés le 11/08/2026 — une seule case « Fait » forçait à ranger
sous le même mot une tâche réussie, une tâche annulée et une décision prise sans travail derrière)*

| Case cochée | `status` | Ce que je fais derrière |
|---|---|---|
| **Fait** | `done` | je solde la `Sortie`, je committe, j'archive |
| **Répondu, pas exécuté** | `answered` | je solde la `Sortie` **et je crée la fiche successeur** avec le travail restant, son owner et son échéance. Son nom va dans `propage:`. Sans fiche successeur, celle-ci **ne part pas au bin** |
| **Annulé** | `killed` | je remplis `raison:`, et je propage **plus** que pour un `done` — « on a décidé de ne pas faire X, parce que Y » est ce qui évite de reposer la question dans trois mois |

**À la clôture, je ne garde que la case cochée** et je retitre la section « État à la clôture — JJ/MM/AAAA ».
Les deux autres options disparaissent : une fiche close n'a plus qu'un état, et l'invariant du bin
(`grep -rln '^- \[ \]' 00-inbox/bin/` ne retourne rien) reste vrai sans exception à retenir.

Si tu coches sans commenter, je fais au mieux avec ce que la fiche contient et **j'écris dans le Fil ce que je
n'ai pas pu établir** : une fiche archivée sans son issue, c'est une information perdue, pas une tâche finie.

**Conventions**
- `status` : `open` → `blocked` → `done` / `answered` / `killed` → archivée dans `00-inbox/bin/AAAA-MM/`
- `owner` : moi · agent · prénom d'un collaborateur — **jamais quelqu'un qui n'a pas été prévenu**
- Nom du fichier : `AAAA-MM-JJ-slug.md`, la date est l'**échéance** → le dossier se trie par urgence.
  Échéance qui bouge = je renomme (Obsidian met les liens à jour) et j'incrémente `reports`. **3ᵉ report = tuer, déléguer ou découper.**
- `closed:` = date de clôture · `propage:` = où la trace a réellement été écrite · `raison:` = pourquoi, si `killed`
- Le nom du fichier **ne change pas** à l'archivage : les wikilinks continuent de résoudre.
- **Ordre de lecture pour l'agent** : `📌 Instructions de l'utilisateur` → `Fait` → `Sortie` → `Fil`.
  L'instruction de l'utilisateur gagne contre tout ce que l'agent a écrit avant.
