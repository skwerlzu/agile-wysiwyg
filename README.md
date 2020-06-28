
## Usage

<h1>NOTE: CUSTOM BUILD</h1>
<p>This version is based on the information below but is a custom build for specific use with a specific project. This is not intended to be a branch of the main project as the changes made will not work universally.
   If you found this git looking for a vue-wysiwyg, please visit the original vue-wysiwyg here <a href="https://github.com/chmln/vue-wysiwyg">https://github.com/chmln/vue-wysiwyg</a>
</p>

### Install agile-wysiwyg

``` bash
meteor npm install agile-wysiwyg@https://github.com/informedecommerce/agile-npm.git --save
```

In your `main.js`:

```js
import wysiwyg from "agile-wysiwyg";
Vue.use(wysiwyg, {}); // config is optional. more below
```

Also make sure to load the stylesheet.
The exact syntax will depend on what preprocessor you use.

```css
@import "~agile-wysiwyg/dist/vueWysiwyg.css";
```

In your components:
```html
<wysiwyg v-model="myHTML" />
```

## Config options

All keys are optional.

```js
{
  // { [module]: boolean (set true to hide) }
  hideModules: { "bold": true },

  // you can override icons too, if desired
  // just keep in mind that you may need custom styles in your application to get everything to align
  iconOverrides: { "bold": "<i class='your-custom-icon'></i>" },

  // if the image option is not set, images are inserted as base64
  image: {
    uploadURL: "/api/myEndpoint",
    dropzoneOptions: {}
  },

  // limit content height if you wish. If not set, editor size will grow with content.
  maxHeight: "500px",

  // set to 'true' this will insert plain text without styling when you paste something into the editor.
  forcePlainTextOnPaste: true,

  // specify editor locale, if you don't specify this, the editor will default to english.
  locale: 'hu'
}
```
Available Modules:
 - bold
 - italic
 - underline
 - justifyLeft
 - justifyCenter
 - justifyRight
 - headings
 - link
 - code
 - orderedList
 - unorderedList
 - image
 - table
 - removeFormat
 - separator

Available Locales:
 - english (default)
 - hungarian
 - dutch
 - german

Note on the image upload API endpoint:
- Image is uploaded by `multipart/form-data`
- Your endpoint must respond back with a string, the URL for the image - e.g. `http://myapp.com/images/12345.jpg`
