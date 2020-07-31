# Symfony
## [Symfony demo](https://github.com/theomeunier/demo-symfony)


# Installer les dépendances

- installer Yarn

```
sudo apt update && sudo apt install yarn
```   

- Installer Webpack

```
yarn add copy-webpack-plugin
```
/

```
yarn add copy-webpack-plugin --dev
```   

Si yarn donner une mauvaise version supprimer tout les dossiers
"sudo rm /usr/bin/yarn" / "sudo rm /usr/bin/yarnpkg"

Puis faire la commande :

```
sudo npm uninstall -g yarn && sudo npm install --global yarn@1.22.4
```

### Jquery

- Intaller Jquery

```
yarn add jquery
```

### Bootstarp

- Intaller Bootstarp

```
yarn add bootstrap
```


- Installer popper

```
yarn add --dev popper.js
```

ajouter dans le template puis dans la rubrique ` {% block stylesheets %}`

```
 {{ encore_entry_link_tags('app') }}
```

 Puis dans la rubrique `{% block javascripts %}`      

 ```
   {{ encore_entry_link_tags('app') }}
```

### composer

- Installer composer

```
composer install
```

- faire les maj
```
composer update
```


# Pour faire du scss

- installer Nodejs

```
sudo apt install nodejs
```

Dans le dossier Webpack enleve le commantaire `.enableSassLoader()`.

Ajouter le `import '../scss/app.scss';` dans le `asset/js/app.js` pour donner le
chemain du fichier.


# Build

- Installer Build

`sudo get install build`

A mettre dans le dossier  `webpack.config.js` une constante
```
const CopyWebpackPlugin = require('copy-webpack-plugin');
```
puis ajooter le plugin dans la rubrique encore
```
.addPlugin(new CopyWebpackPlugin(
        {
        patterns: [
            { from: './assets/image', to: 'image' },
        ],
    }))
```

Il faut définir la variable dans les dossiers `services.yaml`et `twig.yaml`

```
parameters:
    path_directory_image: 'build/image/'
```

ET

```
globals:
     path_image: '%path_directory_image%'
```


## Problème

### Docker

Si le serveur nous domme une errors de logs faire la commande suivant à la racine du projet

```
ls -al
```

Puis crée a nouvrau le dossier "logs" à la racine du projet, puis dans le
dossier crée un fichier "nginx" puis relancer la commande, et faire F5
