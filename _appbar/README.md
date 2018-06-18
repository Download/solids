<!--docs:
title: "Top App Bar"
layout: detail
section: components
excerpt: "A container for items such as application title, navigation icon, and action items."
iconId: toolbar
path: /catalog/top-app-bar/
-->

# Top App Bar

<!--<div class="article__asset">
  <a class="article__asset-link"
     href="https://material-components-web.appspot.com/top-app-bar.html">
    <img src="{{ site.rootpath }}/images/mdc_web_screenshots/top-app-bar.png"
         width="494" alt="Top App Bar screenshot">
  </a>
</div>-->

MDC Top App Bar acts as a container for items such as application title, navigation icon, and action items.

## Design & API Documentation

<ul class="icon-list">
  <li class="icon-list-item icon-list-item--spec">
    <a href="https://material.io/guidelines/components/toolbars.html">Material Design guidelines: Toolbars</a>
  </li>
  <li class="icon-list-item icon-list-item--link">
    <a href="https://material-components-web.appspot.com/top-app-bar.html">Demo</a>
  </li>
</ul>

## Installation

```
npm install @material/top-app-bar
```

## Basic Usage

### HTML Structure

```html
<header class="top-app-bar">
  <div class="mdc-top-app-bar__row">
    <section class="mdc-top-app-bar__section mdc-top-app-bar__section--align-start">
      <a href="#" class="material-icons mdc-top-app-bar__navigation-icon">menu</a>
      <span class="mdc-top-app-bar__title">Title</span>
    </section>
  </div>
</header>
```

### Styles

```scss
@import "../top-app-bar/top-app-bar";
```

### JavaScript Instantiation

```js
import {MDCTopAppBar} from '@material/top-app-bar/index';

// Instantiation
const topAppBarElement = document.querySelector('.top-app-bar');
const topAppBar = new MDCTopAppBar(topAppBarElement);
```

> See [Importing the JS component](../../docs/importing-js.md) for more information on how to import JavaScript.

## Variants

### Top App Bar With Action Items

Top app bars can contain action items which are placed on the side opposite the navigation icon. 

```html
<header class="top-app-bar">
  <div class="mdc-top-app-bar__row">
    <section class="mdc-top-app-bar__section mdc-top-app-bar__section--align-start">
      <a href="#" class="material-icons mdc-top-app-bar__navigation-icon">menu</a>
      <span class="mdc-top-app-bar__title">Title</span>
    </section>
    <section class="mdc-top-app-bar__section mdc-top-app-bar__section--align-end" role="toolbar">
      <a href="#" class="material-icons mdc-top-app-bar__action-item" aria-label="Download" alt="Download">file_download</a>
      <a href="#" class="material-icons mdc-top-app-bar__action-item" aria-label="Print this page" alt="Print this page">print</a>
      <a href="#" class="material-icons mdc-top-app-bar__action-item" aria-label="Bookmark this page" alt="Bookmark this page">bookmark</a>
    </section>
  </div>
</header>
```

### Short

Short top app bars are top app bars that can collapse to the navigation icon side when scrolled.

```html
<header class="top-app-bar top-app-bar--short">
  <div class="mdc-top-app-bar__row">
    <section class="mdc-top-app-bar__section mdc-top-app-bar__section--align-start">
      <a href="#" class="material-icons mdc-top-app-bar__navigation-icon">menu</a>
      <span class="mdc-top-app-bar__title">Title</span>
    </section>
    <section class="mdc-top-app-bar__section mdc-top-app-bar__section--align-end" role="toolbar">
      <a href="#" class="material-icons mdc-top-app-bar__action-item" aria-label="Bookmark this page" alt="Bookmark this page">bookmark</a>
    </section>
  </div>
</header>
```

> Short top app bars should be used with no more than 1 action item.

### Short - Always Closed

Short top app bars can be configured to always appear collapsed by applying the `top-app-bar--short-collapsed` before instantiating the component :

```html
<header class="top-app-bar top-app-bar--short top-app-bar--short-collapsed">
  ...
</header>
```

### Fixed

Fixed top app bars stay at the top of the page and elevate above the content when scrolled. 

```html
<header class="top-app-bar top-app-bar--fixed">
  ...
</header>
```

### Prominent

The prominent top app bar is taller. 

```html
<header class="top-app-bar top-app-bar--prominent">
  ...
</header>
```

## Style Customization

### CSS Classes

Class | Description
--- | ---
`top-app-bar` | Mandatory.
`top-app-bar--fixed` | Class used to style the top app bar as a fixed top app bar.
`top-app-bar--prominent` | Class used to style the top app bar as a prominent top app bar.
`top-app-bar--short` | Class used to style the top app bar as a short top app bar.
`top-app-bar--short-collapsed` | Class used to indicate the short top app bar is collapsed.

### Sass Mixins

Mixin | Description
--- | ---
`top-app-bar-ink-color($color)` | Sets the ink color of the top app bar.
`top-app-bar-icon-ink-color($color)` | Sets the ink color of the top app bar icons.
`top-app-bar-fill-color($color)` | Sets the fill color of the top app bar.
`top-app-bar-fill-color-accessible($color)` | Sets the fill color of the top app bar and automatically sets a high-contrast ink color.
`top-app-bar-short-border-radius($border-radius)` | Sets the `border-bottom-radius` property on the action item side. Used only for the short top app bar when collapsed.

## `MDCTopAppBar` Properties and Methods

MDCTopAppBar does not contain any properties or methods aside from those inherited from MDCComponent.

### Events

Event Name | Event Data Structure | Description
--- | --- | ---
`MDCTopAppBar:nav` | None | Emits when the navigation icon is clicked.

## Usage within Web Frameworks

If you are using a JavaScript framework, such as React or Angular, you can create a Top App Bar for your framework. Depending on your needs, you can use the _Simple Approach: Wrapping MDC Web Vanilla Components_, or the _Advanced Approach: Using Foundations and Adapters_. Please follow the instructions [here](../../docs/integrating-into-frameworks.md).

### `MDCTopAppBarAdapter`

Method Signature | Description
--- | ---
`hasClass(className: string) => boolean` | Checks if the root element of the component has the given className.
`addClass(className: string) => void` | Adds a class to the root element of the component.
`removeClass(className: string) => void` | Removes a class from the root element of the component.
`registerNavigationIconInteractionHandler(evtType: string, handler: EventListener) => void` | Registers an event listener on the native navigation icon element for a given event.
`deregisterNavigationIconInteractionHandler(evtType: string, handler: EventListener) => void` | Deregisters an event listener on the native navigation icon element for a given event.
`notifyNavigationIconClicked() => void` | Emits a custom event `MDCTopAppBar:nav` when the navigation icon is clicked.
`registerScrollHandler(handler) => void` | Registers a handler to be called when user scrolls. Our default implementation adds the handler as a listener to the window's `scroll` event.
`deregisterScrollHandler(handler) => void` | Unregisters a handler to be called when user scrolls. Our default implementation removes the handler as a listener to the window's `scroll` event.
`getViewportScrollY() => number` | Gets the number of pixels that the content of body is scrolled from the top of the page.
`getTotalActionItems() => number` | Gets the number of action items in the top app bar.

### Foundations: `MDCTopAppBarBaseFoundation`, `MDCTopAppBarFoundation`, `MDCFixedTopAppBarFoundation` and `MDCShortTopAppBarFoundation`

The foundations do not contain any public properties or methods aside from those inherited from MDCFoundation. 
