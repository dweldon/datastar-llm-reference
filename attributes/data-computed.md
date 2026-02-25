# `data-computed`

Creates a read-only signal computed from an expression, automatically updated when its dependencies change.

## Syntax

```html
<div data-computed:foo="$bar + $baz"></div>
<div data-computed="{foo: () => $bar + $baz}"></div>
```

Expressions must not perform actions or side effects; use `data-effect` for that.

## Modifiers

| Modifier | Effect |
|----------|--------|
| `__case.camel` | Camel case signal name (default) |
| `__case.kebab` | Kebab case signal name |
| `__case.snake` | Snake case signal name |
| `__case.pascal` | Pascal case signal name |

## Example

```html
<div data-signals="{first: 'Ada', last: 'Lovelace'}"
     data-computed:full-name="$first + ' ' + $last">
  <span data-text="$fullName"></span>
</div>
```
