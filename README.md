# @hi_digital/easy-flex

![npm package version](https://img.shields.io/npm/v/@hi_digital/easy-flex.svg)
![npm downloads](https://img.shields.io/npm/dw/@hi_digital/easy-flex)
![NPM](https://img.shields.io/npm/l/@hi_digital/easy-flex)
![Libraries.io dependency status for latest release, scoped npm package](https://img.shields.io/librariesio/release/npm/@hi_digital/easy-flex)

Easy Flex is a lightweight, simple to use scss grid system based on css flexbox. It is heavily inspired
by [Coffeekraken's gridle v2.0.48](https://github.com/Coffeekraken/gridle/tree/2e6e81e9d10a8dbdc809fe19ea792a532433b5d5)
.

## Table of content

1. [Install](#install)
2. [Quick Start](#quick-start)
3. [Helper Mixins / classes](#helper-mixins--classes)
    1. [Respond-to](#respond-to)
    2. [Show / Hide](#show--hide)
    3. [Prefix / Suffix](#prefix--suffix)
    4. [Push / Pull](#push--pull)
    5. [Order](#order)
    6. [Row justify](#row-justify-content-classes)
    7. [Wrap / no wrap](#row-no-wrap)
    8. [Row reverse](#row-reverse)

## Install

NPM

```
npm install @hi_digital/easy-flex --save-dev
```

YARN

```
yarn add @hi_digital/easy-flex -D
```

## Quick Start

Import easy-flex in scss.

```scss
@import '@hi_digital/easy-flex';
```

Define breakpoints with gutter width and vertical space for the container.

```scss
@include easy-flex-breakpoint('mobile', 480px, 10px, 10px);
@include easy-flex-breakpoint('tablet', 768px, 10px, 10px);
@include easy-flex-breakpoint('laptop', 1024px, 10px, 10px);
@include easy-flex-breakpoint('desktop', 1440px, 10px, 10px);
```

Create the grid with container base values.

```scss
@include create-easy-flex((
        columns: 12,
        container-width: 100%,
        container-max-width: 1920px,
        gutter-width: 10px,
        vertical-space: 10px,
));
```

Use the grid in html. Basic Markup with breakpoints:

```html

<div class="container">
    <div class="row">
        <div class="gr-12 gr-6@tablet">
            content
        </div>

        <div class="gr-12 gr-6@desktop">
            content
        </div>

        <div class="gr-12 gr-6@tablet">
            content
        </div>
    </div>
</div>
```

## Helper Mixins / Classes

There are some helper classes which you can use on each defined breakpoint.

### Respond to

Easy use of media queries in scss files for each defined breakpoint.

```scss
@include respond-to(tablet) {
  property: style;
}  
```

### Show / Hide

```html

<div class="container">
    <div class="row">
        <div class="gr-12 gr-6@desktop hide@tablet show@desktop">
            This column gets hidden @tablet and shown again on @desktop
        </div>

        <div class="gr-6 hide show@tablet">
            This column is hidden until @tablet
        </div>
    </div>
</div>
```

### Prefix / Suffix

The prefix and suffix classes are used to create blanks before or after a grid element.

```html
.prefix-{columns-count}
.prefix-{columns-count}@{breakpoint}
.suffix-{columns-count}
.suffix-{columns-count}@{breakpoint}
```

```html

<div class="container">
    <div class="row">
        <div class="gr-8 suffix-2">
            This has 8 column width and 2 columns dead space to the right
        </div>

        <div class="gr-4 prefix-2@tablet">
            This has 4 column width and @tablet 2 columns dead space to the left
        </div>
    </div>
</div>
```

### Push / Pull

The push and pull classes are used to offset the grid's elements or even swap them.

```html
.push-{columns-count}
.push-{columns-count}@{breakpoint}
.pull-{columns-count}
.pull-{columns-count}@{breakpoint}
```

```html

<div class="container">
    <div class="row">
        <div class="gr-8 push-4">
            This has 8 column width and offset 4 columns to the right
        </div>

        <div class="gr-4 pull-6@tablet">
            This has 4 column width and @tablet offset 6 columns to the left
        </div>
    </div>
</div>
```

### Order

Change the order of the grid elements for each breakpoint. To get this to work properly, every element needs the order
class.

```html
.order-{number}
.order-{number}@{breakpoint}
```

```html

<div class="container">
    <div class="row">
        <div class="gr-6 order-2@tablet">
            First element in markup is the second element displayed @tablet
        </div>
        <div class="gr-6 order-3@tablet">
            Second element in markup is the third element displayed @tablet
        </div>
        <div class="gr-6 order-1@tablet">
            Third element in markup is the first element displayed @tablet
        </div>
    </div>
</div>
```

### Row justify content classes

Sets justify content property on the row for each breakpoint

```html
.row-justify-between
.row-justify-between@{breakpoint}

.row-justify-around
.row-justify-around@{breakpoint}

.row-justify-even
.row-justify-even@{breakpoint}
```

### Row no wrap

Prevent a row from wrapping the columns on each breakpoint

```html
.row-no-wrap
.row-no-wrap@{breakpoint}

.row-wrap@{breakpoint}
```

```html

<div class="container">
    <div class="row row-no-wrap@tablet row-wrap@desktop">
        <div class="gr-12 gr-6@tablet">
            Does not wrap @tablet until @desktop
        </div>

        <div class="gr-12 gr-6@tablet">
            Does not wrap @tablet until @desktop
        </div>
    </div>
</div>
```

### Row reverse

Changes the order of elements in a row

```html
.row-reverse
.row-reverse@{breakpoint}
```

```html

<div class="container">
    <div class="row row-no-wrap@tablet row-wrap@desktop">
        <div class="gr-12 gr-6@tablet">
            Does not wrap @tablet until @desktop
        </div>

        <div class="gr-12 gr-6@tablet">
            Does not wrap @tablet until @desktop
        </div>
    </div>
</div>
```