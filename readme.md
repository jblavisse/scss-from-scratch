# Mise en place de SASS dans un projet HTML/CSS

Ce guide explique comment configurer SASS dans un projet, organiser vos fichiers SCSS en partials (ex: `_header.scss`, `_footer.scss`, `_card.scss`), compiler le SASS en CSS, et utiliser des commandes pour la surveillance et le build.

## Prérequis

Node.js et npm doivent être installés sur votre machine.
Étapes

1. Installation de SASS
   Pour commencer, assurez-vous que vous avez installé SASS dans votre projet via npm. Exécutez la commande suivante dans le terminal à la racine de votre projet :

```bash
npm install sass --save-dev
```

2. Organisation des fichiers SCSS

Créez un répertoire pour vos fichiers SCSS.
Par exemple :

```plaintext
/scss
  _header.scss
  _footer.scss
  _card.scss
  main.scss

/css
  style.css

index.html
```

Les fichiers partiels SCSS commencent par un underscore (`_`) pour indiquer qu'ils sont destinés à être importés dans d'autres fichiers SCSS et ne doivent pas être compilés directement.

Dans le fichier main.scss, vous pouvez importer ces partials comme suit :

```scss
// main.scss
@import "header";
@import "footer";
@import "card";
```

3. Compilation SASS en CSS

Pour compiler votre fichier SCSS principal (main.scss) en CSS:

```bash
npx sass scss/main.scss css/style.css
```

Dans le `index.html`:

```html
<header>
  <link rel="stylesheet" href="css/style.css" />
  ...
</header>
```

4. Utiliser le mode "Watch"

Le mode "watch" permet de surveiller automatiquement les modifications de vos fichiers SCSS et de les recompiler à chaque changement.

Pour activer ce mode, vous pouvez exécuter :

```bash
npx sass scss/main.scss css/style.css --watch
```

Cela surveillera le fichier main.scss et compilera automatiquement à chaque sauvegarde.

5. Ajout des scripts dans package.json

Pour simplifier le processus de développement et de build, vous pouvez ajouter des commandes dans votre fichier package.json :

```json
"scripts": {
"dev": "sass --watch scss/main.sc css/style.css",
"build": "sass scss/main.scss css/style.css --style compressed"
}
}
```

### Commandes à exécuter

- `npm run dev` : Surveillera les changements et recompiler SASS à chaque modification.
- `npm run build` : Compiler SASS en CSS compressé pour un build de production.
