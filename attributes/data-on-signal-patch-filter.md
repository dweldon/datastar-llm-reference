# `data-on-signal-patch-filter`

Filters which signals to watch when using `data-on-signal-patch` by specifying include and/or exclude patterns.

## Syntax

```html
<div data-on-signal-patch-filter="{include: /^counter$/}"></div>
<div data-on-signal-patch-filter="{exclude: /temp$/}"></div>
<div data-on-signal-patch-filter="{include: /user/, exclude: /password/}"></div>
```

## Example

```html
<div data-on-signal-patch-filter="{include: /^counter$/}"
     data-on-signal-patch="console.log('counter changed:', patch)">
</div>
```
