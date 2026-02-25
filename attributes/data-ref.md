# `data-ref`

Creates a signal that is a reference to the DOM element on which the attribute is placed.

## Syntax

```html
<div data-ref:foo></div>
<div data-ref="foo"></div>
```

## Modifiers

| Modifier | Effect |
|----------|--------|
| `__case.camel` | Camel case signal name (default) |
| `__case.kebab` | Kebab case signal name |
| `__case.snake` | Snake case signal name |
| `__case.pascal` | Pascal case signal name |

## Example

```html
<canvas data-ref:canvas></canvas>
<button data-on:click="$canvas.getContext('2d').clearRect(0,0,100,100)">
  Clear
</button>
```
