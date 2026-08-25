# Site académique — solinga87.github.io

Site personnel généré avec [Quarto](https://quarto.org), structuré à
l'image de https://eric-roca.github.io/ (Home / Research / Contact),
avec déploiement automatique vers GitHub Pages via GitHub Actions.

## Structure

- `_quarto.yml` — configuration du site (navigation, thème, titre, langue).
- `index.qmd` — page d'accueil (bio, photo, intérêts de recherche, liens).
- `research.qmd` — liste des publications.
- `contact.qmd` — coordonnées.
- `styles.css` — style visuel.
- `images/` — mettez votre photo ici (`images/avatar.jpg`).
- `.github/workflows/publish.yml` — automatisation : à chaque push sur
  `main`, le site est reconstruit et publié sur la branche `gh-pages`.

## 1. Compléter le contenu

Tous les champs à remplir sont marqués `[À COMPLÉTER : ...]` dans les
fichiers `.qmd`. Remplacez-les par vos informations (nom, titre,
affiliation, bio, publications, liens ORCID/Google Scholar, email...).

Ajoutez votre photo dans `images/avatar.jpg` (vous pouvez alors supprimer
`images/PLACEHOLDER.txt`).

## 2. Prévisualiser en local

Quarto doit être installé (https://quarto.org/docs/get-started/) — c'est
déjà le cas sur cette machine (`quarto --version`).

```bash
quarto preview
```

Cela ouvre un aperçu du site dans votre navigateur avec rechargement
automatique à chaque modification.

Pour un simple test de compilation sans aperçu :

```bash
quarto render
```

## 3. Créer le dépôt GitHub et publier

Cette étape nécessite votre compte GitHub authentifié en local (elle ne
peut pas être faite depuis cet environnement) :

1. Sur GitHub, créez un dépôt public nommé exactement **`solinga87.github.io`**
   (vide, sans README ni licence).
2. Dans ce dossier, connectez le dépôt distant et poussez :

   ```bash
   git remote add origin https://github.com/solinga87/solinga87.github.io.git
   git branch -M main
   git push -u origin main
   ```

3. Sur GitHub, allez dans **Settings → Pages** du dépôt, et réglez
   **Source** sur la branche **`gh-pages`** (elle sera créée automatiquement
   par le premier déploiement du workflow — attendez que l'action
   « Quarto Publish » se termine avec succès dans l'onglet **Actions**,
   puis rechargez la page Settings → Pages si `gh-pages` n'apparaît pas
   encore).
4. Après quelques minutes, le site est accessible à
   **https://solinga87.github.io**.

## 4. Mettre à jour le site ensuite

À chaque modification de contenu :

```bash
git add -A
git commit -m "Mise à jour du contenu"
git push
```

Le workflow GitHub Actions se charge automatiquement de reconstruire et
republier le site — aucune commande `quarto publish` manuelle n'est
nécessaire.
