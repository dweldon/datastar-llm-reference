# `data-effect`

Executes an expression on page load and whenever any signals in the expression change.

## Syntax

```html
<div data-effect="$foo = $bar + $baz"></div>
```

Useful for side effects such as updating signals, making backend requests, or manipulating the DOM.

## Example

```html
<div data-signals="{a: 1, b: 2, sum: 0}"
     data-effect="$sum = $a + $b">
  <span data-text="$sum"></span>
</div>
```
