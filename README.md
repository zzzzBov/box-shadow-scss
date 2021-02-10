# box-shadow() Sass function

The `box-shadow` module is a sass function that can be used to build box-shadow declarations from Sass variable maps.

<details>
  <summary>Table of Contents</summary>

- [box-shadow() Sass function](#box-shadow-sass-function)
  - [API](#api)
    - [Function `box-shadow($box-shadows...)`](#function-box-shadowbox-shadows)
      - [Parameter `$box-shadows`](#parameter-box-shadows)
  - [Examples](#examples)
    - [Single `box-shadow` map](#single-box-shadow-map)
    - [Multiple `box-shadow` maps](#multiple-box-shadow-maps)
    - [`spread` without `blur`](#spread-without-blur)

</details>

## API

### Function `box-shadow($box-shadows...)`

Create a `box-shadow` declaration from a Sass map.

#### Parameter `$box-shadows`

| Meta | Details      |
| ---- | ------------ |
| type | list of maps |

A list of maps describing box-shadows or `none`.

Each map has keys/values of:

| Key    | Type           | Default |
| ------ | -------------- | ------- |
| inset  | boolean        | false   |
| x      | number         | 0       |
| y      | number         | 0       |
| blur   | number or null | null    |
| spread | number or null | null    |
| color  | color or null  | null    |

`inset` is a boolean to toggle the [inset][] keyword.

`x` is a number to specify the [horizontal offset][].

`y` is a number to specify the [vertical offset][].

`blur` is a number to specify the [blur radius][].

`spread` is a number to specify the [spread distance][]. If `spread` is specified, and `blur` is `null`, `blur` will automatically be set to `0`.

`color` is a color to specify the [color][] of the shadow.

## Examples

### Single `box-shadow` map

Passing a single box-shadow map will create a single box-shadow.

```scss
// Sass
@use 'path/to/box-shadow' as *;
.example {
  box-shadow: box-shadow(
    (
      x: 10px,
      y: 10px,
      color: blue,
    )
  );
}

// CSS
.example {
  box-shadow: 10px 10px blue;
}
```

### Multiple `box-shadow` maps

Passing multiple box-shadow maps will add multiple box-shadows.

```scss
// Sass
@use 'path/to/box-shadow' as *;
.example {
  box-shadow: box-shadow(
    (
      x: 10px,
      y: 10px,
      color: blue,
    ),
    (
      x: -10px,
      y: -10px,
      color: red,
    )
  );
}

// CSS
.example {
  box-shadow: 10px 10px blue, -10px -10px red;
}
```

### `spread` without `blur`

If `spread` is specified without `blur`, `blur` will automatically be set to `0`.

```scss
// Sass
@use 'path/to/box-shadow' as *;
.example {
  box-shadow: box-shadow(
    (
      spread: 10px,
    )
  );
}

// CSS
.example {
  box-shadow: 0 0 0 10px;
}
```

[inset]: https://www.w3.org/TR/css-backgrounds-3/#shadow-inset
[horizontal offset]: https://www.w3.org/TR/css-backgrounds-3/#shadow-offset-x
[vertical offset]: https://www.w3.org/TR/css-backgrounds-3/#shadow-offset-y
[blur radius]: https://www.w3.org/TR/css-backgrounds-3/#shadow-blur-radius
[spread distance]: https://www.w3.org/TR/css-backgrounds-3/#shadow-spread-distance
[color]: https://www.w3.org/TR/css-backgrounds-3/#shadow-color
