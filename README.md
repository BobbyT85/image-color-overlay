# image-color-overlay

This is a SASS mixin that takes 2 parameters, a hex value and filter respectively, and applies them to create a color overlay on an image or SVG class.

The mixin initially generates a greyscale filter for backup use then uses SVG `feColorMatrix` (as of September 2022 [feColorMatrix isn't currently supported by Safari](https://caniuse.com/?search=fecolormatrix)) for precise color conversion using the hex value that is passed in and is applied as a filter. 

It then uses a media query to check if the browser is Safari then overwrites the filter that is generated in the step above with the one that is passed in.

The Safari specific filter can be generated from the CodePen below, though trial and error will be needed to calculate a value that is as close to the target hex as it is likely that an exact match won't be generated
> https://codepen.io/sosuke/pen/Pjoqqp 

It can then be passed into the mixin though trial and error may be needed to reach the target color as it's almost likely that it won't match the target hex value.

<br>

## Install

```bash
npm install image-color-overlay
```

<br>

## Usage

```scss
.image {
    $safari-filter: invert(23%) sepia(100%) saturate(4587%) hue-rotate(296deg) brightness(118%) contrast(109%);
    @include image-color-overlay(#00ffff, $safari-filter);
}
```

<br>

[![NPM Version][npm-image]][npm-url]

[npm-image]: https://img.shields.io/npm/v/image-color-overlay.svg
[npm-url]: https://npmjs.org/package/image-color-overlay