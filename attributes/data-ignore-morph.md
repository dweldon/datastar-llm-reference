# `data-ignore-morph`

Tells the PatchElements watcher to skip an element and its children when morphing the DOM.

## Syntax

```html
<div data-ignore-morph>
  <!-- This element will not be morphed -->
</div>
```

## Example

```html
<div id="content">
  <div data-ignore-morph>
    <!-- Preserved during server-driven DOM patches -->
    <video autoplay></video>
  </div>
</div>
```
