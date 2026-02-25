# `data-on-intersect`

Executes an expression when the element enters or exits the viewport.

## Syntax

```html
<div data-on-intersect="$visible = true"></div>
```

## Modifiers

| Modifier | Effect |
|----------|--------|
| `__once` | Triggers only once |
| `__exit` | Triggers when element leaves the viewport |
| `__half` | Triggers when 50% visible |
| `__full` | Triggers when fully visible |
| `__threshold.N` | Triggers at N% visibility (e.g., `.25`, `.75`) |
| `__delay.Nms` / `__delay.Ns` | Delays execution |
| `__debounce.Nms` | Debounces; sub-modifiers: `.leading`, `.notrailing` |
| `__throttle.Nms` | Throttles; sub-modifiers: `.noleading`, `.trailing` |
| `__viewtransition` | Wraps in `document.startViewTransition()` |

## Example

```html
<div data-on-intersect__once__full="@get('/api/lazy-content')">
  Loading...
</div>
```
