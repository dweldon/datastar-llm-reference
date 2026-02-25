# `data-init`

Executes an expression upon initialization (page load, DOM patches, or when the attribute changes).

## Syntax

```html
<div data-init="$count = 1"></div>
```

## Modifiers

| Modifier | Effect |
|----------|--------|
| `__delay.Nms` / `__delay.Ns` | Postpones execution by N milliseconds or seconds |
| `__viewtransition` | Wraps execution in `document.startViewTransition()` |

## Example

```html
<div data-signals:count="0"
     data-init__delay.500ms="$count = 1">
  <span data-text="$count"></span>
</div>
```
