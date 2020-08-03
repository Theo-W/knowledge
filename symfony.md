# Symfony

## Création projet symfony

### Installation

- Installation du package de symfony skeleton

```
composer create-project symfony/website-skeleton {nom_du_pojet}
```

- Importer les fichiers de docker: https://github.com/theomeunier/stack_docker_symfony

- Construire les services docker

```
docker-compose up --build -d
```

# Installer les dépendances

## Installation

- Installer Webpack Encore

```
composer require symfony/webpack-encore-bundle
yarn install
```

## Configuration scss

Dans le dossier Webpack enleve le commantaire `.enableSassLoader()`.

- Commande d'instllation

```
yarn add sass-loader@^8.0.0 node-sass --dev
```

Ajouter la ligne suivante `import '../scss/app.scss';` dans le ficher `asset/js/app.js`.



## Bootstarp 4.x

### Installation

- Intaller Bootstarp et ces dépencances

```
yarn add bootstrap --dev
```

- Intaller Jquery

```
yarn add jquery --dev
```

- Installer Popper.js

```
yarn add --dev popper.js
```

### Configuration

importer jquery, popper.js, bootstrap,

```
import $ from 'jquery';
import popper from 'popper.js';
import bootstrap from 'bootstrap';
```

importer bootstrap dans `assets/scss/app.scss`

```
@import "~bootstrap/scss/bootstrap";
```

### Configuration des templates

Ajouter dans le template `base.html.twig`, dans le block ` {% block stylesheets %}`:

```
 {{ encore_entry_link_tags('app') }}
```

 Puis dans le block `{% block javascripts %}`:     

```
   {{ encore_entry_script_tags('app') }}
```


# Build

- Environement dev
```
yarn dev
```

- Environement dev avec l'option 'watch'
```
yarn watch
```

- Environement de production
```
yarn build
```

## Copie des fichiers statiques

### Installation

commande d'Installation

```
yarn add copy-webpack-plugin --dev
```

### Configuration

A mettre dans le fichier `webpack.config.js` une constante:

```
const CopyWebpackPlugin = require('copy-webpack-plugin');
```

puis ajouter le plugin dans la rubrique `Encore`

```
.addPlugin(new CopyWebpackPlugin(
        {
        patterns: [
            { from: './assets/image', to: 'image' },
        ],
    }))
```

### Configuration du path image

Il faut définir la variable dans les fichers de configuration  `config/services.yaml`et `config/packages/twig.yaml`

```
parameters:
    path_directory_image: 'build/image/'
```

ET

```
globals:
     path_image: '%path_directory_image%'
```
