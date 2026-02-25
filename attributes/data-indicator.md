# `data-indicator`

Creates a signal that is `true` during active fetch requests and `false` otherwise, enabling loading state visualization.

## Syntax

```html
<button data-indicator:fetching></button>
<button data-indicator="fetching"></button>
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
<button data-on:click="@get('/api/data')"
        data-indicator:fetching
        data-attr:disabled="$fetching">
  Load
</button>
<div data-show="$fetching">Loading...</div>
```
