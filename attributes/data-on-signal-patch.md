# `data-on-signal-patch`

Executes an expression whenever any signals change. The `patch` variable contains details about the signal modification.

## Syntax

```html
<div data-on-signal-patch="console.log('Signal changed:', patch)"></div>
```

## Modifiers

| Modifier | Effect |
|----------|--------|
| `__delay.Nms` / `__delay.Ns` | Delays execution |
| `__debounce.Nms` | Debounces; sub-modifiers: `.leading`, `.notrailing` |
| `__throttle.Nms` | Throttles; sub-modifiers: `.noleading`, `.trailing` |

## Example

```html
<div data-on-signal-patch__debounce.500ms="@post('/api/auto-save')">
</div>
```
