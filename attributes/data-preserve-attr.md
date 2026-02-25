# `data-preserve-attr`

Preserves the value of one or more attributes when morphing DOM elements.

## Syntax

```html
<details open data-preserve-attr="open"></details>
```

Multiple attributes can be preserved by separating them with spaces.

## Example

```html
<details open class="expanded" data-preserve-attr="open class">
  <summary>Collapsible</summary>
  <p>This stays open through DOM patches.</p>
</details>
```
