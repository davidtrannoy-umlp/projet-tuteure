# Conventions du projet — Refonte infocombesancon.fr

Ce fichier documente les conventions établies pour ce projet, afin que tout travail futur sur ce site (nouvelles pages, mises à jour) reste cohérent avec ce qui a été fait.

## Contexte du projet

Site MkDocs (thème Material) servant de **brief / cahier des charges** pour un projet tutoré BUT Info-Com : refonte du site [infocombesancon.fr](https://infocombesancon.fr) avec Elementor. Projet géré par le tuteur seul (les étudiants consultent le site, ne contribuent pas au dépôt). Démarrage : rentrée de septembre, équipe de 6-7 étudiant·es.

Dépôt : `https://github.com/davidtrannoy-umlp/projet-tuteure` · Publié sur `https://davidtrannoy-umlp.github.io/projet-tuteure/`

## Structure du site

```
docs/
├── index.md                    → Accueil : vue d'ensemble du projet
├── 01-contexte/                → Le site actuel, ses constats
├── 02-cadrage/                 → Objectifs, équipe, planning
├── 03-analyse-prealable/       → Trames méthodo : cibles, audit, benchmark
├── 04-refonte/                 → Cadre technique Elementor, livrables
├── 05-ressources/              → Contacts, outils, glossaire
└── assets/                     → Images (captures d'écran, schémas)
```

Ne pas créer de nouveau chapitre numéroté sans l'ajouter à la fois dans `mkdocs.yml` (section `nav`) et dans cette liste.

## Conventions éditoriales

- **Ton** : clair, pédagogique, à destination d'étudiant·es de 2ᵉ année de BUT Info-Com (pas de jargon non expliqué).
- **Blocs admonition** utilisés systématiquement pour varier le rendu et signaler l'intention :
  - `!!! note` — information de contexte
  - `!!! tip` — conseil méthodologique
  - `!!! warning` — point de vigilance / piège à éviter
- **Pages "trame à remplir"** (notamment dans `03-analyse-prealable/`) : toujours commencer par un bloc `!!! note "Trame à remplir par l'équipe"` explicite, puis fournir une structure (tableaux, checklists `- [ ]`) plutôt que des paragraphes vides — l'équipe doit pouvoir éditer directement sans deviner le format attendu.
- **Pas de contenu sensible** : ne jamais inscrire d'identifiants/accès dans les pages (le site est public sur GitHub Pages). Toujours renvoyer vers [Ressources](docs/05-ressources/index.md) qui rappelle cette règle.
- **Liens internes** entre chapitres systématiques (`[texte](../chapitre/page.md)`) pour relier les pages entre elles plutôt que les laisser isolées.

## Workflow technique (spécifique à cette machine Windows)

À reproduire pour toute nouvelle session de travail sur ce projet :

1. **Toujours utiliser des chemins absolus ou `cd` explicite vers la racine du dépôt** avant `git`/`mkdocs`. Le répertoire de travail du shell peut dériver entre deux appels d'outils, ce qui a déjà causé une fois la création de dossiers dupliqués imbriqués (`08- Projet tuteuré/08- Projet tuteuré/...`). Toujours vérifier `pwd` et la structure avec `find . -maxdepth 3` après toute création de fichier/dossier un peu complexe, avant de commit.
2. **Git sur ce repo nécessite** :
   - `git config --global http.sslbackend schannel` (problème de certificat SSL avec le backend par défaut)
   - `git config --global --add safe.directory 'P:/_tools/Obsidian/IUT/08- Projet tuteuré'` (dossier sur lecteur réseau/mappé)
3. **Avant tout commit** : `mkdocs build` doit passer sans erreur, puis `rm -rf site/` (le dossier `site/` est généré et ignoré via `.gitignore`, ne jamais le committer).
4. **Captures d'écran** : pas d'outil de navigateur/capture intégré disponible. Solution de contournement utilisée : service `image.thum.io` (gratuit, sans clé) :
   ```bash
   curl --ssl-no-revoke -sL "https://image.thum.io/get/width/1200/<URL>" -o capture.png
   ```
   ⚠️ Le premier appel renvoie souvent une image de chargement (placeholder thum.io) — toujours **relire l'image générée** avant de l'utiliser, et relancer la requête après quelques secondes si besoin. Le flag `--ssl-no-revoke` est nécessaire sur cette machine (échec de vérification de révocation de certificat sinon).
   Images stockées dans `docs/assets/`.
5. Le déploiement est automatique (`.github/workflows/deploy.yml`) : un simple `git push` sur `main` republie le site en 1-2 minutes. Ne jamais faire de `mkdocs gh-deploy` manuel (risque de thème par défaut si l'environnement local n'a pas `mkdocs-material`).

## Historique des décisions

- Le dépôt est géré uniquement par le tuteur (pas d'accès étudiants au repo) — décision prise lors du cadrage initial.
- Les pages d'analyse préalable sont volontairement laissées en trame vide plutôt que pré-remplies, pour que le travail d'analyse soit réellement fait par l'équipe à la rentrée.
- Le planning (`02-cadrage/planning.md`) liste les étapes mais laisse toutes les dates vides : aucune échéance n'était encore fixée au moment de la création du site.
