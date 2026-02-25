# `data-json-signals`

Renders the text content of an element as a reactive JSON representation of signals, useful for debugging.

## Syntax

```html
<!-- All signals -->
<pre data-json-signals></pre>

<!-- Filtered -->
<pre data-json-signals="{include: /user/}"></pre>
<pre data-json-signals="{exclude: /temp$/}"></pre>
```

## Modifiers

| Modifier | Effect |
|----------|--------|
| `__terse` | Outputs compact JSON without extra whitespace |

## Example

```html
<div data-signals="{count: 0, name: 'test'}">
  <pre data-json-signals="{include: /^count/}"></pre>
  <pre data-json-signals__terse></pre>
</div>
```
