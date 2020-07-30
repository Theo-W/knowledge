# Symfony
## [Symfony demo](https://github.com/theomeunier/demo-symfony)

## Faire les mise à jours

```
composer update
```    


# Installer les dépendances

- installer Yarn

```
sudo apt update && sudo apt install yarn
```   

- Installer Yarn

```
sudo install yarn
```

- Installer Webpack

```
yarn add copy-webpack-plugin
```
/

```
yarn add copy-webpack-plugin --dev
```   

- Intaller Bootstarp

```
yarn add bootstarp
```

### Jquery

- Intaller Jquery

```
yarn add jquery
```

- Installer popper

```
yarn add --dev popper.js
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
