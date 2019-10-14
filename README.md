# Flexgrid - a simple grid based on flexbox layout

[![Build Status](https://travis-ci.org/moso/flexgrid.svg?branch=master)](https://travis-ci.org/moso/flexgrid)

No more floats! Regular grid layout is based on both block and inline flow directions, however, the flexbox (or just flex) layout is based on "flex-flow directions". Thus `float` and `clear` have no effect. Using `float` causes the `display`-property to compute to `block`. Using `flexbox` also means less JavaScript! And everything is, of course, responsive and stacks perfectly.

**Please note:** Flexbox is only partially supported by IE10. Any IE-version lower than 10 does not support flexbox. However, Flexgrid utilizes the power of `autoprefixer`, so IE10 is relatively safe with prefixes. More info on [Can I Use](http://caniuse.com/#search=flex).

### Changelog

**3.0.1 (2019-10-14)**
- Renamed `_flexgrid` to `_gridgenerator` after discovering some `@import` issues in external projects because of name clashing
- Updated dependencies

**3.0.0 (2019-10-09)**
- Complete transition to webpack
- Rewrite of the grid generator
- Simplified alignment class names
- Added optional margin utilities
- Added `space-evenly` (note: no support in IE, `space-between` is used as fallback)
- Ditched Tailwind syntax (use 2.x branch if you need it)
- Discarded demo files - use the new documentation website

Older changelogs can be found in the 2.x branch.

## Documentation

You find everything fully documented at the new [Docs page](https://docs.flexgrid.io).

## Packages

Use your favorite package manager to install Flexgrid

NPM:
```bash
$ npm install --save flexgrid.io
```

Yarn:
```bash
$ yarn add flexgrid.io
```

You can then easily import Flexgrid to your existing Sass/SCSS file:
```scss
@import 'flexgrid.io/src/flexgrid';
```

## CDN

You can find Flexgrid on most public CDNs that cache npm packages, like unpkg:
```html
<link rel="stylesheet" href="https://unpkg.com/flexgrid.io@3.0.0/dist/flexgrid.min.css">
```

You can also link directly to the latest build hosted on my own site:
```html
<link rel="stylesheet" href="https://flexgrid.io/dist/3.0.0/flexgrid.min.css">
```
Keep in mind that this build is the full build including margin utilities.

### v2.5.2

If you for some reason want the latest old version, you can easily install it with NPM/Yarn as well:
```bash
$ npm install --save flexgrid.io@2.5.2 # yarn add flexgrid@2.5.2
```

## Classes

Flexgrid comes with 5 easy recognizable classes, if you're familiar with [Bootstrap]:
- xs (xtra small - for mobile devices and small tablets)
- sm (small - for large mobile devices and tablets)
- md (medium - for tablets and very small laptops)
- lg (large - for smaller laptops and -desktops)
- xl (xlarge - for desktops)

The classes can be combined to create more dynamic and flexible layouts.

**Pro tip**: Each class scales up, so if you wish to set the same widths for `sm` and `md`, you only need to specify `sm`.

## .container and .container-fluid

Flexgrid comes with responsive containers that boxes the content in which are controlled by `@media`-queries. These `@media`-queries trigger at the same widths defined by the [Bootstrap](https://getbootstrap.com)-framework. However, as a small detail, Flexgrid bases its width-triggers on `rem` instead of `px`. This creates a much more fluid layout. While `em` is relative to the `font-size` of its direct or nearest parent, `rem` is only relative to the `html` (root) `font-size`. Flexgrid `font-size` is set to `16px`. There is also a fluid container that has no `@media`-queries.

```html
<!-- Container -->
<div class="container">
  ...
</div>

<!-- Container fluid -->
<div class="container-fluid">
  ...
</div>
```

## Row

The row is where it all happens. Whether you want to align your content, or you simply just want columns, the `.row`-class is the one that sets `display: flex`.

## Columns

Flexgrid comes with columns with percent-based widths allow fluid resizing of columns and rows. Rows acts as alignment containers.

![columns](https://flexgrid.io/old/img/columns.png)

```html
<div class="container">
  <div class="row">
    <div class="md-12">.md-12</div>
    <div class="md-11">.md-11</div>
    <div class="md-1">.md-1</div>
    ...
    <div class="md-6">.md-6</div>
    <div class="md-6">.md-6</div>
    ...
  </div>
</div>
```

## Alignment, offsets, margin, etc

Flexgrid comes with a lot built-in methods to align your content the way you like it. It's never been easier to "center-center" your content. You can even offset columns or reorder them - and this follows the same pattern of being responsive and scalable.

It also comes with an optional utility toolbox where you can use margin as a way to offset/align your content. If you want these enabled, look below.

## Limitations

*__Flexgrid is not a framework__*, thus you won't find every single flexbox property in Flexgrid. As per the name, Flexgrid revolves around being a grid for building layouts. It \*does\* come with some of the most used properties, like alignment, offsets, margin utilities, etc. But to save space and to stick with the scope of the project, you won't find classes that sets `display: flex` on elements, handles `flex-direction`, `flex-wrap`, and so on. I trust you to handle these yourself should you want to build more advanced layouts. However, there are mixins inside the source code for all of these, and thus very easy to build in the classes yourself.

A good example is the flexbox mixin found in `/src/mixins/_flexgrid-mixins.scss`:
```scss
@mixin flexbox {
    display: flex;
}
```

If you want expand Flexgrid and build a class into it that, in this case, sets `display: flex`, it can easily be done by using the mixin:

```scss
.flex {
    @include flexbox();
}
```

Just remember to `@import` the mixins if you're not just editing the source (see below).

## Editing the source

It's easy to modify the source. Clone this repository and edit away. Flexgrid comes with [webpack](https://webpackjs.org) that compiles the source for you with a single command.

If you want margin utilities enabled, just set the `$enable-utils`-variable to `true` and recompile. This variable can even be overwritten in your own SCSS-variables file if you're using Flexgrid as part of a project, as it's got the `!default`-flag. Just remember to import Flexgrid before your own variables.

##### Requirements

Compiling the source requires a terminal, and [Node.js](https://nodejs.org) at least v10 (LTS), or [Yarn](https://yarnpkg.com).

To install the dependencies, you just run:
```bash
$ npm install # yarn install
```

When you're done editing, you just run:
```bash
$ npm run build # yarn run build
```

This will compile a regular `.css`-file, and a minified `.min.css`-file to the `/dist`-folder.

## Contributing

PR's are ~~welcome~~ encouraged.

## License

[MIT](https://github.com/moso/flexgrid/blob/master/LICENSE)
