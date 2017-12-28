# Styleguide-and-CSS-Standards
best practices and coding standards


Table of contents
=================

  * [Introduction](#gh-md-toc)
    * [Goals](#installation)
  * [Table of contents](#table-of-contents)
  * [Commonly used frameworks and libraries](#table-of-contents)
  * [File Structure](#installation)
  * [Typography](#typography)
  * [Bootstrap](#bootstrap)
    * [Grid](#installation)
    * [Components within grid](#multiple-files)
  * [CSS Guidelines](#installation)
    * [Syntax and Formatting](#multiple-files)
    * [Naming Conventions](#multiple-files)
    * [Titling](#multiple-files)
    * [Commenting](#multiple-files)
  * [SASS Guidelines](#installation)
     * [Syntax and Formatting](#multiple-files)
    * [Naming Conventions](#multiple-files)
    * [Titling](#multiple-files)
    * [Commenting](#multiple-files)
    * [Common Utility Functions](#multiple-files)
  * [React Guidelines](#installation)
  * [Resources](#multiple-files)
  
Common frameworks and libraries
============

...

File Structure
============

...

Typography
============

Bootstrap
============

### Grid
Bootstrap’s grid system uses a series of containers, rows, and columns to layout and align content.

```html
<div class="container">    
 <div class="row">                            <!---Rows must always be in a container-->
  <div class="col-lg-12 col-md-6 col-sm-12">  <!---Columns must always be in a row-->
   ...
  </div>
 </div>
</div>
```
Rows should always be in containers and columns should always be within rows due to bootstrap using negative margins. This will cause unexpected layout issues if you do not follow this pattern. Without going into terrible detail, if you want to read more about bootstraps containers, rows, and columns or want to learn about pulls and pushes visit:

http://www.helloerik.com/the-subtle-magic-behind-why-the-bootstrap-3-grid-works

http://getbootstrap.com/

### Components within bootstraps grid
All components should be built without widths and heights. This means that we can let the grid provide the layout and the component can be reused throughout the site in different areas without breaking. The grid system should be separated from all components. The grid is only used for layout. For example:




**Bad**

```html
<div class="col-lg-12 some-class">
 ...
</div>
```

**Good**

```html
<div class="col-lg-12">
 <div class="some-class">
  ...
 </div>
</div>
```
CSS
============

### !important

We generally try to stay away from using !important due to specificity issues. However there will be times when !important is needed for quick fixes. When this is the case we should always put our !importants in the shame.scss file (see shame.css). All use of !important should be well documented and eventually refactored when time permits.

### Titling

Each section should have a corresponding section title which is prefixed with a hash (#) symbol to make searching for a specific section easier. This practice also goes for file seperated sections where the section title would be at the top of each section file.

```css
/*------------------------------------*\
  #SECTION-TITLE
\*------------------------------------*/

.lol-wut {

}
```

SASS
============

### Common Utility Functions

**Px to Em**

```css
/*un-modified*/

@function calc-em($target-px, $context) {
  @return ($target-px / $context) * 1em;
}

/*and modified to accept a base context variable*/

$browser-context: 16;

@function em($pixels, $context: $browser-context) {
  @return ($pixels / $context) * 1em;
}

```
**Color Theme Generator**

```css

@mixin bg-colors($map) {
  @each $theme, $color in $map {
    &--#{$theme} {
      background-color: $color;
    }
  }
}

```

```css

/*Example*/

$ui-colors: (
key       : value,
default   : color,
success   : color,
error     : color,
warning   : color,
info      : color
);

.btn {
   @include bg-colors($ui-colors)
}
/*Outputs*/
.btn--default {
  background-color: #ffffff;
}
.btn--success {
  background-color: #ffffff;
}
.btn--error {
  background-color: #ffffff;
}
```

**Color Palett Map Retriever**

```css

@function palette($palette, $shade: 'base') {
  @return map-get(map-get($palettes, $palette), $shade);
}


$palettes: (
  grey: (
   xx-light : lighten(#fffeee, 43%),
   x-light  : lighten(#fffeee, 33%),
   light    : lighten(#fffeee, 13%),
   base     : $grey,
   dark     : darken(#fffeee, 8%)
   x-dark   : darken(#fffeee, 16%)
  ),
  black: (
   light    : lighten(#fffeee, 10%),
   base     : $black,
   dark     : darken($black, 10%)
  )
);
```

```css
/*Example*/

h1 {
 color: palette(grey, x-dark);
}

h1 {
 color: palette(grey, light);
}
```

React
============

...
