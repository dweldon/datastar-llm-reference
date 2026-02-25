# `data-ignore`

Tells Datastar to ignore an element and its descendants during DOM walking and plugin application.

## Syntax

```html
<div data-ignore>
  <!-- Datastar skips this and all descendants -->
</div>
```

## Modifiers

| Modifier | Effect |
|----------|--------|
| `__self` | Ignores only the element itself, not its descendants |

## Example

```html
<div data-ignore>
  <div data-third-party-lib>
    <!-- Datastar will not process anything here -->
  </div>
</div>
```
