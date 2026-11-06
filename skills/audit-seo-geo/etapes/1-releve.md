# Étape 1 · Relevé du site

**But** : lire le site tel qu'il est aujourd'hui et remplir `fiche-site.md`, la base de toutes les autres étapes.
On ne juge presque rien ici : on relève, avec les preuves.

## À faire

1. **Page d'accueil.** `curl -sIL` pour le code final et la chaîne de redirections (http vers https, avec ou sans
   www). Puis `curl -sL` pour en tirer, valeurs exactes : title, meta description, H1, canonical, types JSON-LD
   (`@type`), liens du pied de page (réseaux sociaux compris). Si le HTML est presque vide (site rendu en
   JavaScript), relire dans le navigateur et le noter.
2. **Fichiers racine** : codes HTTP de `/robots.txt`, `/sitemap.xml` (et `/sitemap_index.xml` en cas de 404),
   `/llms.txt`. Le détail est pour l'étape 3 ; ici on note juste ce qui répond.
3. **Pages importantes** : 5 à 10, prises dans le menu et le sitemap (offre, tarifs, à propos, contact, blog, FAQ).
   Pour chacune : URL, title, H1, code HTTP.
4. **Ordre de grandeur de l'index** : `site:domaine` dans Google (navigateur, google.fr). C'est une estimation, on
   l'écrit comme telle.
5. **Search Console**, seulement si le cadrage l'a autorisé : 20 pages et 20 requêtes avec le plus d'impressions
   sur 3 mois, pages indexées contre pages envoyées. Si l'ouverture échoue, dire ce qui a bloqué et ce que l'utilisateur
   doit faire pour débloquer.
6. **Type d'activité** : confirmer celui du cadrage avec ce qu'on lit (tableau ci-dessous). Il oriente les
   étapes suivantes.
7. Remplir `modeles/fiche-site.md` dans `audit-livrables/<slug>/fiche-site.md`.

## Le type d'activité oriente tout l'audit

| Type | Ce qui pèse le plus |
|---|---|
| **Local** | fiche Google, avis, nom-adresse-téléphone identiques partout, pages par ville, requêtes « service + ville » |
| **SaaS** | pages produit, comparatifs et « alternative à X », documentation publique, avis G2/Capterra, Reddit |
| **E-commerce** | pages catégorie et produit, données Product et avis, guides d'achat, requêtes d'achat |
| **Service B2B** | pages par service, cas clients chiffrés, méthode, LinkedIn de l'entreprise et des dirigeants |
| **Service B2C** | preuves sociales fortes, FAQ rassurante, pages locales si l'activité l'est |
| **Média** | catégories, pages auteur, fraîcheur, données Article |
| **Marque personnelle** | page « à propos » qui prouve, requête « prénom nom », LinkedIn personnel, réalisations datées |

Si le site ne rentre dans aucune case, l'écrire et demander.

## Seuil d'arrêt

Si la page d'accueil n'a pu être lue ni par curl, ni par le navigateur, ni par un copier-coller du client, la fiche
est **provisoire**, la note de l'étape est de 4 au plus, et on prévient avant de lancer la suite : les étapes
suivantes ne valent que ce que vaut ce relevé.

## Note de l'étape

Elle mesure la fiabilité du relevé, pas la qualité du site.

Compte rendu : `1-releve.md` (format dans `regles.md`) + `fiche-site.md`.
