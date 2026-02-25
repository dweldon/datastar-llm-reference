# `data-attr`

Sets HTML attribute values to expressions and keeps them in sync as values change.

## Syntax

```html
<div data-attr:aria-label="$foo"></div>
<div data-attr="{'aria-label': $foo, disabled: $bar}"></div>
```

## Example

```html
<div data-signals:name="'Datastar'">
  <a data-attr:title="$name" href="#">Hover me</a>
  <button data-attr="{disabled: $name == '', 'aria-label': $name}">
    Submit
  </button>
</div>
```
