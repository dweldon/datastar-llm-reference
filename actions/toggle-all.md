# `@toggleAll()`

Toggles the boolean value of all matching signals.

## Signature

```
@toggleAll(filter?: { include: RegExp, exclude?: RegExp })
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `filter.include` | `RegExp` | Pattern matching signal paths to include |
| `filter.exclude` | `RegExp` | Pattern matching signal paths to exclude |

## Example

```html
<div data-signals="{isOpen: false, isActive: true}">
  <button data-on:click="@toggleAll({include: /^is/})">
    Toggle all
  </button>
</div>
```
