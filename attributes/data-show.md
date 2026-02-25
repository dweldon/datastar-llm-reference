# `data-show`

Shows or hides an element based on whether an expression evaluates to `true` or `false`.

## Syntax

```html
<div data-show="$foo"></div>
```

Add `style="display: none"` to prevent flickering before Datastar processes the DOM.

## Example

```html
<div data-signals:visible="false">
  <button data-on:click="$visible = !$visible">Toggle</button>
  <p data-show="$visible" style="display: none">Now you see me.</p>
</div>
```
