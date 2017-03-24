# Styleguide-and-CSS-Standards
best practices and coding standards


Table of contents
=================

  * [Introduction](#gh-md-toc)
    * [Goals](#installation)
    * [Resources](#multiple-files)
  * [Table of contents](#table-of-contents)
  * [Bootstrap](#bootstrap)
  * [Installation](#installation)

  


### Rule declaration

A “rule declaration” is the name given to a selector (or a group of selectors) with an accompanying group of properties. Here's an example:

```css
.listing {
  font-size: 18px;
  line-height: 1.2;
}
```


**Bad**

```css
.avatar{
    border-radius:50%;
    border:2px solid white; }
.no, .nope, .not_good {
    // ...
}
#lol-no {
  // ...
}
```

**Good**

```css
.avatar {
  border-radius: 50%;
  border: 2px solid white;
}

.one,
.selector,
.per-line {
  // ...
}
```

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

Installation
============
