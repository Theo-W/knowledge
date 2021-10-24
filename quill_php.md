# QuillJs with PHP

## Installation QuillJS and PHP-QUILL-RENDERER
```shell
npm install quill
composer require deanblackborough/php-quill-renderer
```

## Configuration
1 - Create a quill.js file in the js folder of your application and add the following configuration
```js
import Quill from 'quill/core';
import Toolbar from 'quill/modules/toolbar';
import Snow from 'quill/themes/snow';
import Bold from 'quill/formats/bold';
import Italic from 'quill/formats/italic';
import Header from 'quill/formats/header';

Quill.register({
    'modules/toolbar': Toolbar,
    'themes/snow': Snow,
    'formats/bold': Bold,
    'formats/italic': Italic,
    'formats/header': Header
});

export default Quill;
```

2 - importer le quilljs dans le fichier app.js
```js
require('quill')
const Quill = require("quill");
```
## QuillJS and PHP-QUILL-RENDERER
1 - Configuration input
```html
<label for="content" class="form-label">Content</label>
<textarea id="content" name="content" hidden></textarea>
<div id="editor-container" style="height: 250px"></div>
```

2 - Custom input with quill
```js
let quill = new Quill('#editor-container', {
    modules: {
        toolbar: [
            ['bold', 'italic', 'underline', 'strike'],
            ['link', 'blockquote', 'code-block', 'image'],
            [{list: 'ordered'}, {list: 'bullet'}],
            [{ 'script': 'sub'}, { 'script': 'super' }],      // superscript/subscript
            [{ 'indent': '-1'}, { 'indent': '+1' }],          // outdent/indent
            [{ 'direction': 'rtl' }],                        // custom dropdown
            [{ 'header': [1, 2, 3, 4, 5, 6, false] }],
            [{'color': []}, {'background': []}],          // dropdown with defaults from theme
        ]
    },
    theme: 'snow'
});
```

3 - We transfer the information in input hide
```js
let form_admin_training = document.querySelector('#form_admin_training');
form_admin_training.addEventListener('submit', function (e) {
    let content = document.querySelector('textarea[name=content]');
    content.value = JSON.stringify(quill.getContents());
    return false;
});
```

4 - We transform the json into html
```php
use DBlackborough\Quill\Render;

$training = Training::find($id);
$quill = new Render($training->content);
$training_content = $quill->render();
```

5 - We pass it in the view and we recover it
```html
<div>
   <p>{!! $training_content !!}</p>
</div>
```