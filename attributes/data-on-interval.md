# `data-on-interval`

Repeatedly executes an expression at a specified time interval (default: 1 second).

## Syntax

```html
<div data-on-interval="$count++"></div>
```

## Modifiers

| Modifier | Effect |
|----------|--------|
| `__duration.Nms` / `__duration.Ns` | Sets the interval (default: `1s`) |
| `__duration.leading` | Executes immediately on the first interval |
| `__viewtransition` | Wraps in `document.startViewTransition()` |

## Example

```html
<div data-signals:seconds="0"
     data-on-interval__duration.500ms="$seconds++">
  <span data-text="$seconds"></span>
</div>
```
