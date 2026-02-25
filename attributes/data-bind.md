# `data-bind`

Creates a signal (if one doesn't already exist) and sets up two-way data binding between it and an element's value.

## Syntax

```html
<input data-bind:foo />
<input data-bind="foo" />
```

Works with `input`, `select`, `textarea`, and web components. File inputs automatically encode contents as base64 with the format `{ name, contents, mime }[]`.

## Modifiers

| Modifier | Effect |
|----------|--------|
| `__case.camel` | Camel case signal name (default) |
| `__case.kebab` | Kebab case signal name |
| `__case.snake` | Snake case signal name |
| `__case.pascal` | Pascal case signal name |

## Example

```html
<input data-bind:foo-bar />
<!-- Creates $fooBar signal (camelCase by default) -->

<div data-signals:choice="'10'">
  <select data-bind:choice>
    <option value="10">Ten</option>
    <option value="20">Twenty</option>
  </select>
  <span data-text="$choice"></span>
</div>
```
