<!--docs:
title: "Lists"
layout: detail
section: components
excerpt: "Lists present multiple line items vertically as a single continuous element."
iconId: list
path: /catalog/lists/
-->

# Lists

<!--<div class="article__asset">
  <a class="article__asset-link"
     href="https://material-components-web.appspot.com/list.html">
    <img src="{{ site.rootpath }}/images/mdc_web_screenshots/lists.png" width="365" alt="Lists screenshot">
  </a>
</div>-->

MDC List provides styles which implement [Material Design Lists](https://material.io/go/design-lists) -
"A single continuous column of tessellated subdivisions of equal width." Both single-line and two-line lists are
supported (with three-line lists [planned](https://github.com/material-components/material-components-web/issues/31)).
MDC Lists are designed to be accessible and RTL aware.

## Design & API Documentation

<ul class="icon-list">
  <li class="icon-list-item icon-list-item--spec">
    <a href="https://material.io/go/design-lists">Material Design guidelines: Lists</a>
  </li>
  <li class="icon-list-item icon-list-item--link">
    <a href="https://material-components-web.appspot.com/list.html">Demo</a>
  </li>
</ul>

## Installation
```
npm install @material/list
```

## Usage

### HTML Structure

#### Single-Line List
A basic list consists simply of the list itself, and list items taking up one line.

List items (rows) can contain primary and secondary actions. Lists items can contain 1 supporting graphic tile and/or 1 metadata tile that are positioned at the start and end of the list item, respectively.


```html
<ul class="solid_list">
  <li class="list_item">Single-line item</li>
  <li class="list_item">Single-line item</li>
  <li class="list_item">Single-line item</li>
</ul>
```

#### Two-Line List
While in theory you can add any number of "lines" to a list item, you can use the `list_two_line` combined with some extra markup around the text to style a list in the two-line list style as defined by [the spec](https://material.io/go/design-lists#lists-specs) (see "Two-line lists").

```html
<ul class="solid_list list_two_line">
  <li class="list_item">
    <span class="list_item_text">
      First-line text
      <span class="list_item_secondary_text">
        Second-line text
      </span>
    </span>
  </li>
  <li class="list_item">
    <span class="list_item_text">
      First-line text
      <span class="list_item_secondary_text">
        Second-line text
      </span>
    </span>
  </li>
  <li class="list_item">
    <span class="list_item_text">
      First-line text
      <span class="list_item_secondary_text">
        Second-line text
      </span>
    </span>
  </li>
</ul>
```

#### List Groups
Multiple related lists can be grouped together using the `list_group` class on a containing element.

```html
<div class="list_group">
  <h3 class="list_group_subheader">List 1</h3>
  <ul class="solid_list">
    <li class="list_item">line item</li>
    <li class="list_item">line item</li>
    <li class="list_item">line item</li>
  </ul>

  <h3 class="list_group_subheader">List 2</h3>
  <ul class="solid_list">
    <li class="list_item">line item</li>
    <li class="list_item">line item</li>
    <li class="list_item">line item</li>
  </ul>
</div>
```

#### List Dividers
MDC List contains an `list_divider` class which can be used as full-width or inset subdivisions either within lists themselves, or standalone between related groups of content.

```html
<ul class="solid_list">
  <li class="list_item">Item 1 - Division 1</li>
  <li class="list_item">Item 2 - Division 1</li>
  <li role="separator" class="list_divider"></li>
  <li class="list_item">Item 1 - Division 2</li>
  <li class="list_item">Item 2 - Division 2</li>
</ul>
```

> NOTE: the role="separator" attribute on the list divider. It is important to include this so that assistive technology can be made aware that this is a presentational element and is not meant to be included as an item in a list. Note that separator is indeed a valid role for li elements.

OR

```html
<ul class="solid_list">
  <li class="list_item">Item 1 - List 1</li>
  <li class="list_item">Item 2 - List 1</li>
</ul>
<hr class="list_divider">
<ul class="solid_list">
  <li class="list_item">Item 1 - List 2</li>
  <li class="list_item">Item 2 - List 2</li>
</ul>
```

### CSS Classes
CSS Class | Description
--- | ---
`solid_list` | Mandatory, for the list element
`list_non_interactive` | Optional, disables interactivity affordances
`list_dense` | Optional, styles the density of the list, making it appear more compact
`list_avatar_list` | Optional, configures the leading tiles of each row to display images instead of icons. This will make the graphics of the list items larger
`list_two_line` | Optional, modifier to style list with two lines (primary and secondary lines)
`list_item` | Mandatory, for the list item element
`list_item_text` |	Optional, primary text for the row (displayed as middle column of the list item)
`list_item_secondary_text` | Optional, secondary text for the list item. Displayed below the primary text. Should be the child of `list_item_text`
`list_item_selected` | Optional, styles the row in an selected* state
`list_item_activated` | Optional, styles the row in an activated* state
`list_item_graphic` | Optional, the first tile in the row (in LTR languages, the first column of the list item). Typically an icon or image.
`list_item_meta`	| Optional, the last tile in the row (in LTR languages, the last column of the list item). Typically small text, icon. or image.
`list_group` | Optional, wrapper around two or more solid_list elements to be grouped together
`list_group_subheader` |	Optional, heading text displayed above each list in a group
`list_divider` | Optional, for list divider element
`list_divider_padded` | Optional, leaves gaps on each side of divider to match padding of `list-item__meta`
`list_divider_inset` | Optional, increases the leading margin of the divider so that it does not intersect the avatar column

> NOTE: `list_divider` class can be used between list items (example 1) *OR* between two lists (example 2)

> NOTE: the difference between selected and activated states:

* *Selected* state should be implemented on the `.list-item` when it is likely to change soon. Eg., selecting one or more photos to share in Google Photos.
* Multiple items can be selected at the same time when using the *selected* state
* *Activated* state is similar to selected state, however should only be implemented once within a specific list.
* *Activated* state is more permanent than selected state, and will **NOT** change soon relative to the lifetime of the page.

### Sass Mixins
Mixin | Description
--- | ---
`list_item_primary_text_ink_color($color)` | Sets the ink color of the primary text of the list item
`list_item_secondary_text_ink_color($color)` | Sets the ink color of the secondary text of the list item
`list_item_graphic_fill_color($color)` | Sets background ink color of the graphic element within list item
`list_item_graphic_ink_color($color)` | Sets ink color of the graphic element within list item
`list_item_meta_ink_color($color)` | Sets ink color of the meta element within list item
`list_divider_color($color)` | Sets divider ink color
`list_group_subheader_ink_color($color)` | Sets ink color of subheader text within list group
