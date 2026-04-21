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
| `__prop.<name>` | Bind to a specific writable property (camelCased) instead of the default. |
| `__event.<name>` | Choose which event(s) sync the element back to the signal. Chainable. |

`__prop` and `__event` may be used independently or together, and are useful for web components and non-standard inputs.

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

<!-- Custom element: bind to the `checked` property, sync on `change` -->
<my-toggle data-bind:is-checked__prop.checked__event.change></my-toggle>

<!-- Sync on multiple events -->
<input data-bind:query__event.input.change />
```
