# solids
#### CSS-only Material Design Primitives

[![npm](https://img.shields.io/npm/v/solids.svg)](https://npmjs.com/package/solids)
[![license](https://img.shields.io/npm/l/solids.svg)](https://creativecommons.org/licenses/by/4.0/)
![installs](https://img.shields.io/npm/dt/solids.svg)
![mind BLOWN](https://img.shields.io/badge/mind-BLOWN-ff69b4.svg)

<sup><sub><sup><sub>.</sub></sup></sub></sup>

![logo](solids.png)

## Install

```sh
npm install --save solids
```

## Use

To use `solids` styles in your app, I recommend [webpack](https://webpack.js.org/) with the [sass-loader](https://github.com/webpack-contrib/sass-loader). Make sure to import the required `solids` sass files in your code. Always import the base styles from `solids/solids` and any additional styles for the components you are
using.

### Import

You can import the solids styles from some sass file in your project:

*index.scss*
```css
@import "solids/solids";
@import 'solids/appbar';

/* your own styles */
```

Alternatively, you can import the solids styles from some JS file in your project:

*index.js*
```js
import "solids/solids";
import 'solids/appbar';

/* your javascript code */
```

### Render markup

Allmost all the markup for solids is static. Meaning you render it once and from there on it stays the same. This is unline in MDC-web, where all sorts of behaviors are triggered by toggling CSS class names on the component. In solids, we only use CSS class names to configure the component, but not to manage its state.

Make sure to render your components within an element with `class="solids"`:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Example</title>
  </head>
  <body>
    <!-- establish a `solids` context -->
    <div class="solids">
      <!-- render `solids` components -->
      <header class="appbar">
        <!-- ... -->
      </header>

      <!-- ... -->
    </div>
  </body>
</html>
```

To keep the markup simple and CSS class names short, all `solids` CSS classes are combined with the `.solids` class so they are scoped to only work within the `class="solids"` context element. For example, the appbar styles selectors look like:

```css
.solids .appbar {
  /* only targets elements with class="appbar" within elements with class="solids"
}
```

### Using with Preact
If you are using [Preact](https://preactjs.com), check out [preact-solids](https://npmjs.com/package/preact-solids) which can render the markup for you.

### Using with CSS Modules
If you are using the CSS Modules loader, you need to use the correct class names as transformed by the CSS Modules loader when rendering the HTML. To facilitate building components that support both forms, with and without CSS modules, each `solids` component publishes a JS file in addition to the SASS files which contains an object in the same format as produced by CSS Modules with the default class names used in the component. For example, for the AppBar component, we have `solids/appbar/classes.js`:

*solids/appbar/classes.js*
```js
module.exports = {
	appbar: 'appbar',
	fixed: 'fixed',
	dense: 'dense',
	prominent: 'prominent',
	short: 'short',
	collapsed: 'collapsed',
	has_action: 'has_action',
	shrink: 'shrink',
	floating: 'floating',
	start: 'start',
	end: 'end',
	reserve: 'reserve',
	title: 'title',
	icon: 'icon',
	action: 'action',
	tactile: 'tactile',
};
```

You can use this object as a public interface for rendering your markup:

```js
import classes from 'solids/appbar/classes'

function render() {
  return `
    <header class="${classes.appbar}">
      <!-- ... -->
    </header>
  `
}
```

When using CSS Modules, you would import the classes directly from the styles:

```js
import classes from 'solids/appbar'

function render() {
  return `
    <header class="${classes.appbar}">
      <!-- ... -->
    </header>
  `
}
```

You can even combine this with [preact-context](https://npmjs.com/package/preact-context) or something similar to create components that support both CSS Modules or unscoped class names or even a mix at the same time! Have a look at how `preact-solids` implements this with its `preact-solids/theme` component.


## Issues

Add an issue in the [issue tracker](https://github.com/download/solids/issues)
to let me know of any problems you find, or questions you may have.


## Credits

Credits go to:
* The Material Design and MDC teams at Google
* [Ben Mildren](https://github.com/mildrenben) for inspiring the world with [Surface](https://mildrenben.github.io/surface/).
* [Jason Miller](https://github.com/developit) for building [Preact](https://preactjs.com)
* [Prateek Bhatnagar](https://github.com/prateekbh) for building [preact-material-components](https://github.com/prateekbh/preact-material-components)


## Copyright

© 2019 by [Stijn de Witt](http://StijnDeWitt.com). Some rights reserved.


## License

Licensed under the [MIT](https://opensource.org/licenses/MIT) Open Source license.
