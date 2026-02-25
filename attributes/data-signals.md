# `data-signals`

Patches (adds, updates, or removes) one or more signals into the existing signal store.

## Syntax

```html
<div data-signals:foo="1"></div>
<div data-signals:foo.bar="1"></div>
<div data-signals="{foo: {bar: 1, baz: 2}}"></div>
<div data-signals="{foo: null}"></div>
```

Values defined later in the DOM override earlier ones. Setting `null` or `undefined` removes a signal. Signals prefixed with `_` are excluded from backend requests by default. Signal names cannot contain double underscores.

## Modifiers

| Modifier | Effect |
|----------|--------|
| `__case.camel` | Camel case signal name (default) |
| `__case.kebab` | Kebab case signal name |
| `__case.snake` | Snake case signal name |
| `__case.pascal` | Pascal case signal name |
| `__ifmissing` | Only patches if the key doesn't already exist |

## Example

```html
<div data-signals="{count: 0, name: 'world'}">
  <div data-signals:count__ifmissing="99">
    <!-- count stays 0 because it already exists -->
  </div>
  <span data-text="$name"></span>
</div>
```
