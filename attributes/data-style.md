# `data-style`

Sets inline CSS style values on an element based on expressions and keeps them in sync.

## Syntax

```html
<div data-style:display="$hiding && 'none'"></div>
<div data-style:background-color="$red ? 'red' : 'blue'"></div>
<div data-style="{
  display: $hiding ? 'none' : 'flex',
  'background-color': $red ? 'red' : 'green'
}"></div>
```

Empty strings, `null`, `undefined`, or `false` restore the original inline style or remove the property.

## Example

```html
<div data-signals:highlight="false">
  <button data-on:click="$highlight = !$highlight">Toggle</button>
  <p data-style:background-color="$highlight ? 'yellow' : ''">
    Highlight me
  </p>
</div>
```
