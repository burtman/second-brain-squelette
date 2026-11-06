# Étape 3 · Technique et accès des robots IA

**But** : vérifier que Google et les IA peuvent lire le site, et le lisent comme il faut. Les fichiers racine se
testent tout de suite, sans rien demander (règle 4).

## 1. Les fichiers, en une passe

```bash
UA="Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/130.0 Safari/537.36"
DOM="https://exemple.fr"
for p in /robots.txt /sitemap.xml /sitemap_index.xml /sitemap-index.xml /llms.txt /llms-full.txt \
         /.well-known/security.txt /favicon.ico; do
  printf '%-28s ' "$p"
  curl -s -o /dev/null -A "$UA" -w '%{http_code} %{size_download}o %{url_effective}\n' -L "$DOM$p"
done
curl -sIL -A "$UA" "$DOM/sitemap.xml" | grep -i '^last-modified'
```

Un 200 qui renvoie une page HTML (la page d'accueil, une page d'erreur habillée) n'est pas un fichier présent :
vérifier le contenu. Un sitemap peut aussi être déclaré dans `robots.txt` sous un autre nom : le lire.

| Fichier | Si présent | Avant de conclure « absent » |
|---|---|---|
| robots.txt | lire chaque bloc `User-agent` | 2 essais, dont un dans le navigateur |
| sitemap | compter les URL, regarder les dates | tester les 3 noms ci-dessus et la ligne `Sitemap:` du robots.txt |
| llms.txt | lire les 30 premières lignes, tester ses liens | tester aussi llms-full.txt et chercher `site:domaine llms` |
| JSON-LD | lister les `@type` | page d'accueil **et** 2 pages internes, puis validator.schema.org |

## 2. La matrice des robots IA

Un site peut tout faire bien et rester invisible pour une IA si son `robots.txt` ou son pare-feu bloque le robot
qui va chercher les pages. Pour chaque robot, déterminer la règle qui s'applique (son bloc dédié, sinon
`User-agent: *`) : **Autorisé**, **Bloqué** ou **Non spécifié**.

| Robot | Rôle | Si bloqué |
|---|---|---|
| OAI-SearchBot | recherche ChatGPT | **faille prioritaire** : la marque sort des réponses de ChatGPT |
| PerplexityBot | recherche Perplexity | **faille prioritaire** |
| Claude-SearchBot | recherche Claude | **faille prioritaire** |
| ChatGPT-User, Perplexity-User, Claude-User | visite à la demande d'un utilisateur | l'IA ne peut pas ouvrir la page qu'on lui montre |
| GPTBot, ClaudeBot, CCBot, Applebot-Extended, Bytespider | entraînement des modèles | **un choix**, pas une faille : protège le contenu, sans effet sur ce qui est déjà appris |
| Google-Extended | entraînement de Gemini | un choix ; **sans effet** sur Google Search et les AI Overviews |
| Googlebot | Google Search et AI Overviews | ne jamais recommander de le bloquer |

Si `robots.txt` n'a pas pu être lu, toute la matrice est `Non vérifié`. Jamais « tout est ouvert » par défaut.

**Le pare-feu peut contredire le robots.txt.** Un indice, pas une preuve : rejouer la page d'accueil avec le
User-Agent du robot.
```bash
for bot in "OAI-SearchBot/1.0" "PerplexityBot/1.0" "Claude-SearchBot/1.0" "GPTBot/1.1"; do
  printf '%-22s ' "$bot"; curl -s -o /dev/null -w '%{http_code}\n' -A "Mozilla/5.0 (compatible; $bot)" "$DOM/"
done
```
Un 403 ici peut venir d'un blocage du robot **ou** d'une protection contre l'usurpation (le vrai robot arrive
d'adresses IP que le pare-feu reconnaît). Statut `Déduit`, et le signaler comme point à vérifier dans les journaux
du serveur ou la console du CDN.

## 3. Le reste

- **Redirections** : http vers https, avec et sans www, avec et sans barre finale. Une seule version doit
  répondre 200, les autres redirigent en 301 vers elle.
- **Canonical** sur l'accueil et les pages de l'échantillon : présent, et pointe vers soi-même ou la bonne version.
- **Titles, meta, H1** des pages de l'échantillon : tableau page par page.
- **Index** : ordre de grandeur `site:` contre nombre d'URL du sitemap (`Déduit`). Search Console si l'accès existe.
- **Performance** : l'API PageSpeed, sans navigateur. Sans clé, le quota anonyme est partagé et souvent épuisé
  (erreur 429) : créer une clé gratuite dans Google Cloud et la mettre en `PAGESPEED_API_KEY` dans le `.env` (jamais committé). Un appel mobile, un appel ordinateur.

```bash
# depuis la racine du dépôt
KEY=$(grep '^PAGESPEED_API_KEY=' .env | cut -d= -f2- | tr -d "\"'")
for s in mobile desktop; do
  curl -s --max-time 90 "https://www.googleapis.com/pagespeedonline/v5/runPagespeed?url=$DOM&strategy=$s&key=$KEY" \
  | python3 -c "import sys,json;d=json.load(sys.stdin);e=d.get('error');r=d.get('lighthouseResult',{});a=r.get('audits',{});print('$s','ERREUR '+e['message'][:100] if e else 'score %d · LCP %s · CLS %s · TBT %s'%(r['categories']['performance']['score']*100,a['largest-contentful-paint']['displayValue'],a['cumulative-layout-shift']['displayValue'],a['total-blocking-time']['displayValue']))"
done
```

  En cas d'échec : pagespeed.web.dev dans le navigateur. Sinon `Non vérifié`. Jamais un score supposé.
- **Mobile** : lisibilité et taille des zones cliquables, au navigateur en largeur téléphone.
- **Plusieurs langues** : balises hreflang présentes, réciproques, avec une version `x-default`. Sinon « non
  applicable ».
- **Fraîcheur** : date de publication et de mise à jour visibles sur les contenus, et dans `datePublished` /
  `dateModified` du JSON-LD.

## 4. Données structurées : quoi recommander

| Type d'activité | Types utiles |
|---|---|
| Local | Organization, LocalBusiness, BreadcrumbList |
| SaaS | Organization, SoftwareApplication, BreadcrumbList |
| E-commerce | Organization, Product, AggregateRating (seulement sur des avis réels et visibles), BreadcrumbList |
| Service B2B ou B2C | Organization, Service, Article pour le blog, BreadcrumbList |
| Média | Organization, Article ou NewsArticle, Person pour les auteurs |
| Marque personnelle | Person avec un `sameAs` complet, Article |

FAQPage seulement si la page a une vraie FAQ. L'effet des données structurées sur les citations des IA est
discuté (voir `reference/chiffres.md`) : on les recommande pour que les machines comprennent la page et pour les
résultats enrichis de Google, jamais comme une garantie d'être cité.

## llms.txt

Fichier récent, sans effet prouvé à ce jour, peu coûteux. Le recommander sans le survendre. Modèle minimal :
```
# <Marque>

> <Ce que fait la marque, en une ou deux phrases.>

## Pages principales
- [Accueil](https://…): <une phrase>
- [<Offre principale>](https://…): <une phrase>
- [Tarifs](https://…): <une phrase>
- [À propos](https://…): <qui est derrière, depuis quand>
```

## Note de l'étape

Un robot de recherche IA bloqué, ou un site que Google ne peut pas indexer, plafonne la note à 3.

Compte rendu : `3-technique.md`, avec un bloc par fichier (URL testée, code HTTP, date, verdict).
