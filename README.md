# @hi_digital/easy-flex

![npm package version](https://img.shields.io/badge/version-v1.6.0-blue)
![NPM](https://img.shields.io/badge/license-MIT-brightgreen)
![dependency status](https://img.shields.io/librariesio/release/npm/@hi_digital/easy-flex)
![Twitter URL](https://img.shields.io/twitter/url?style=social&url=https%3A%2F%2Fhi-schweiz.ch)

Easy Flex is a lightweight, simple to use scss grid system based on css flexbox. It is heavily inspired
by [Coffeekraken's gridle v2.0.48](https://github.com/Coffeekraken/gridle/tree/2e6e81e9d10a8dbdc809fe19ea792a532433b5d5)
.

[Easy Flex Demo Page](https://easy-flex.netlify.app/)

## Table of content

1. [Install](#install)
2. [Quick Start](#quick-start)
3. [Mixins](#mixins)
    1. [Respond-to](#respond-to)
    2. [Add custom class](#add-custom-class)
4. [Helper classes](#helper-classes)
    1. [Show / Hide](#show--hide)
    2. [Prefix / Suffix](#prefix--suffix)
    3. [Push / Pull](#push--pull)
    4. [Order](#order)
    5. [Row justify](#row-justify-content-classes)
    6. [Row align](#row-align-items-classes)
    7. [Wrap / no wrap](#row-no-wrap)
    8. [Row reverse](#row-reverse)
    9. [No gutter](#no-gutter)

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
@include easy-flex-breakpoint('tiny', 480px, 10px, 10px);
@include easy-flex-breakpoint('small', 768px, 10px, 10px);
@include easy-flex-breakpoint('medium', 1024px, 10px, 20px);
@include easy-flex-breakpoint('large', 1200px, 10px, 20px);
@include easy-flex-breakpoint('huge', 1440px, 20px, 40px);
@include easy-flex-breakpoint('full', 1680px, 20px, 40px);
```

Create the grid with container base values.

```scss
@include create-easy-flex((
        columns: 12,
        container-width: 100%,
        container-max-width: 1680px,
        gutter-width: 10px,
        vertical-space: 10px,
));
```

Use the grid in html. Basic Markup with breakpoints:

```html

<div class="container">
    <div class="row">
        <div class="gr-12 gr-6@small">
            content
        </div>

        <div class="gr-12 gr-6@large">
            content
        </div>

        <div class="gr-12 gr-6@small">
            content
        </div>
    </div>
</div>
```

## Mixins

There are some helper classes which you can use on each defined breakpoint.

### Respond to

Easy use of media queries in scss files for each defined breakpoint.

```scss
@include respond-to(small) {
  property: style;
}  
```

### Add custom class

Adds a custom class for each breakpoint.

```scss
@include easy-add-class(name) {
  property: style;
}
```

#### Example

```scss
@include easy-add-class(tac) {
  text-align: center !important;
}
```

#### Usage

```html

<div class="container">
    <div class="row">
        <div class="gr-12 gr-6@small tac@small">
            This column gets hidden @small and shown again on @large
        </div>
    </div>
</div>
```

## Helper Classes

### Show / Hide

```html

<div class="container">
    <div class="row">
        <div class="gr-12 gr-6@large hide@small show@large">
            This column gets hidden @small and shown again on @large
        </div>

        <div class="gr-6 hide show@small">
            This column is hidden until @small
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

        <div class="gr-4 prefix-2@small">
            This has 4 column width and @small 2 columns dead space to the left
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

        <div class="gr-4 pull-6@small">
            This has 4 column width and @small offset 6 columns to the left
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
.order-first
.order-first@{breakpoint}
.order-last
.order-last@{breakpoint}
```

```html

<div class="container">
    <div class="row">
        <div class="gr-6 order-2@small">
            First element in markup is the second element displayed @small
        </div>
        <div class="gr-6 order-3@small">
            Second element in markup is the third element displayed @small
        </div>
        <div class="gr-6 order-1@small">
            Third element in markup is the first element displayed @small
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

.row-justify-end
.row-justify-end@{breakpoint}

.row-justify-center
.row-justify-center@{breakpoint}
```

### Row align items classes

Sets align items property on the row for each breakpoint

```html
.row--align-center
.row--align-center@{breakpoint}

.row-align-start
.row-align-start@{breakpoint}

.row--align-end
.row--align-end@{breakpoint}

.row-align-stretch
.row--align-stretch@{breakpoint}

.row-align-baseline
.row-align-baseline@{breakpoint}
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
    <div class="row row-no-wrap@small row-wrap@large">
        <div class="gr-12 gr-6@small">
            Does not wrap @small until @large
        </div>

        <div class="gr-12 gr-6@small">
            Does not wrap @small until @large
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
    <div class="row row-no-wrap@small row-wrap@large">
        <div class="gr-12 gr-6@small">
            Does not wrap @small until @large
        </div>

        <div class="gr-12 gr-6@small">
            Does not wrap @small until @large
        </div>
    </div>
</div>
```

### No gutter

Removes the padding or padding left / right from grid elements

```html
.no-gutter
.no-gutter-left
.no-gutter-right

.no-gutter@{breakpoint}
.no-gutter-left@{breakpoint}
.no-gutter-right@{breakpoint}
```

```html

<div class="container">
    <div class="row">
        <div class="gr-12 gr-6@small no-gutter-right@large">
            Removes the padding right @large
        </div>

        <div class="gr-12 gr-6@small no-gutter-left@large">
            Removes the padding left @large
        </div>
    </div>
</div>
```