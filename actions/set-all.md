# `@setAll()`

Sets the value of all matching signals to the provided value.

## Signature

```
@setAll(value: any, filter?: { include: RegExp, exclude?: RegExp })
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `value` | `any` | Value to assign to matching signals |
| `filter.include` | `RegExp` | Pattern matching signal paths to include |
| `filter.exclude` | `RegExp` | Pattern matching signal paths to exclude |

## Example

```html
<div data-signals="{user: {name: '', nickname: ''}}">
  <button data-on:click="@setAll('', {include: /^user\./})">
    Clear user fields
  </button>
</div>
```
