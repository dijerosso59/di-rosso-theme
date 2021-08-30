# Custom-theme-WP

Custom-theme-WP est un thème WordPress spécialement configuré avec Tailwind.css.

```bash
git clone https://github.com/dijerosso59/Custom-WP.git
```

## Quickstart

1. Créer un Virtual Host WordPress
2. Dans le dossier wp-content/themes, coller le dossier du custom-theme-WP

## Configuration de Tailwind

Définissez les fichiers qui seront purgé par Tailwind avec l'élément <b>purge</b> :

```js
module.exports = {
  mode: 'jit',
  purge: ['../**/*.php'],
  darkMode: 'class', // or 'media' or 'class'
  theme: {
    fontFamily: {
      'patrick': ['Patrick Hand', 'cursive']
    },
    extend: {},
  },
  variants: {
    extend: {},
  },
  plugins: [],
}
```

## Modification du CSS
Tout d'abord, assurez-vous de mettre le nom de votre thème en début de code

Ensuite, vous travaillez uniquement avec le fichier dev.css. Il suffit d'ajouter vos règles et votre css custom à l'intérieur du layer components :

```css
/*
Theme Name: Tailwind-WP
*/

@tailwind base;
@tailwind components;
@tailwind utilities;

@layer components {

  .btn {
    @apply bg-red-500 text-3xl rounded;
  }
  
  @screen md {
  
    .btn {
      @apply px-5 py-4
    }
  
  }
  
}
```
Une fois votre travaille terminé, ouvrez un terminal dans le dossiet assets et executez cette commande :

```bash
npx tailwindcss -i ./dev.css -o ../style.css -w
```

Cela va analyser le comportement de TailWind de tous les fichiers configurés précédemment avec l'élément purge et mettra à jour le fichier style.css à la racine du thème.