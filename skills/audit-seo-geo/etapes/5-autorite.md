# Étape 5 · Autorité, entité, réputation

**But** : mesurer ce que le reste du web dit de la marque. Les IA citent surtout ce qui est confirmé par plusieurs
sources extérieures. C'est l'étape qui produit le plus de faux négatifs : le protocole de la règle 5 s'applique
à chaque plateforme, sans exception.

## 1. Présences, plateforme par plateforme

| Famille | Plateformes |
|---|---|
| Réseaux | LinkedIn entreprise, LinkedIn des fondateurs, Instagram, X, Facebook, TikTok, Pinterest |
| Vidéo | YouTube : la chaîne de la marque **et** les vidéos de tiers qui la mentionnent (`site:youtube.com "marque"`) |
| Discussions | Reddit (sous-forum de la marque, fils qui la citent), Quora, forums du secteur |
| Avis | fiche Google, Trustpilot, Avis Vérifiés ; G2 et Capterra pour un logiciel |
| Bases de référence | Wikipedia (fr et en), Wikidata, Crunchbase, Product Hunt |
| Annuaires | PagesJaunes et annuaires du secteur si l'activité est locale |
| Presse | `"marque" site:lesechos.fr OR site:journaldunet.com OR site:maddyness.com OR site:bfmtv.com` et presse du secteur |

Pour chacune : URL testée, verdict sur l'échelle de la règle 5, ce qu'on a vu (abonnés, dernière publication,
note et nombre d'avis), et l'action (maintenir, densifier, activer, créer).

## 2. La fiche Google, si l'activité est locale

La chercher de 4 façons avant de conclure : recherche « marque ville » sur Google (encart à droite), recherche dans
Google Maps, lien `g.page` ou Maps présent sur le site, ouverture dans le navigateur. Introuvable après les quatre :
le constat est « fiche non trouvée, à créer », c'est une action, pas un trou de l'audit.

Si elle existe, relever : nom exact, catégorie principale et secondaires, adresse, téléphone, site lié, horaires,
note, nombre d'avis, date des derniers avis, réponses du propriétaire, photos récentes, publications récentes.
Un champ illisible est `Non vérifié`, pas absent.

**Nom, adresse, téléphone** : identiques au caractère près sur le site, la fiche Google, les annuaires et les
réseaux ? Lister chaque écart avec son URL.

## 3. L'entité

Les IA rattachent plus facilement une marque qu'elles reconnaissent comme une entité bien définie.
- **Wikidata** : chercher la marque. Si elle a un identifiant (Q…), relever la description et vérifier que le
  site officiel déclaré est le bon. Ne jamais inventer un identifiant.
- **Panneau de connaissance Google** : la recherche de la marque affiche-t-elle un encart ? Titre, catégorie,
  liens affichés.
- **Cohérence** : même nom, même phrase de description sur le site, dans le `sameAs`, sur la fiche Google, les
  réseaux et Wikidata. Lister les divergences.

## 4. Les comparatifs tiers

Les articles « meilleur X », « top X 2026 », « alternatives à <leader> » sont repris tels quels par les IA quand on
leur demande une recommandation. Chercher 3 à 5 de ces requêtes sur google.fr, ouvrir les articles de tiers qui
sortent (médias, blogs du secteur, comparateurs), et noter : la marque y est-elle ? quels concurrents y sont ? à
quel rang ? Un article qui cite deux concurrents et oublie la marque est une cible d'approche prioritaire.

## 5. Ce qui se laisse influencer

Classer chaque source repérée, ici et à l'étape 7 :
- **Direct** : la marque agit seule et vite (son site, ses profils, sa chaîne, sa fiche Google, ses pages d'avis,
  une participation sincère sur Reddit ou Quora).
- **Indirect** : il faut convaincre quelqu'un (presse, comparatifs tiers, podcasts, vidéos d'autres créateurs,
  Wikipedia si la marque remplit les critères de notoriété).
- **Hors de portée pour l'instant** : sites concurrents, médias fermés, Wikipedia sans notoriété suffisante.

## 6. Reddit et forums

Si c'est pertinent pour l'activité : 3 sous-forums où la cible parle, et 3 sujets concrets (un fil existant à
enrichir, ou un message long et utile, sans lien commercial). Compte avec un historique réel ; jamais de
compte créé pour l'occasion.

## Garde-fous propres à l'étape

- Jamais de mention presse, d'avis ou de lien inventé.
- Jamais d'achat ou d'échange d'avis, ni de campagne d'avis agressive.
- Faible audience n'est pas absence.
- Une marque avec une ou deux présences actives ne peut pas avoir moins de 4 : la note suit les faits.

Compte rendu : `5-autorite.md`, terminé par le journal du protocole : plateformes testées, variantes de nom
essayées, méthodes, `sameAs` et pied de page lus.
