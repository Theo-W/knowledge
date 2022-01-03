# Bootstrap with Symfony

- install webpack-encore `composer require symfony/webpack-encore-bundle`
- install bootstrap `npm install bootstrap --save`
- install pooperjs `npm i @popperjs/core`
- install sass-loader `npm install sass-loader sass webpack --save-dev`

- Rename style.css through style.scss
- import bootstrap in style.scss `@import "~bootstrap/scss/bootstrap";`
- Activate option sass in `webpack.config.js` => `.enableSassLoader()
- import boostrap in `assets/app.js`
```js
import './styles/style.scss';
import '@popperjs/core';
import 'bootstrap';
```
- import files Js and Sass in `base.html.twig`
```php
{% block stylesheets %}
      {{ encore_entry_link_tags('app') }}
{% endblock %}

{% block javascripts %}
      {{ encore_entry_script_tags('app') }}
{% endblock %}
```
- Run server dev `npm run dev`