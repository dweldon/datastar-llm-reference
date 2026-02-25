# `data-class`

Adds or removes CSS classes from elements based on expression evaluation.

## Syntax

```html
<div data-class:font-bold="$foo == 'strong'"></div>
<div data-class="{success: $foo != '', 'font-bold': $foo == 'strong'}"></div>
```

## Modifiers

| Modifier | Effect |
|----------|--------|
| `__case.camel` | Camel case class name |
| `__case.kebab` | Kebab case class name (default) |
| `__case.snake` | Snake case class name |
| `__case.pascal` | Pascal case class name |

## Example

```html
<div data-signals:status="'ok'">
  <p data-class:text-green="$status == 'ok'"
     data-class:text-red="$status == 'error'">
    Status indicator
  </p>
</div>
```
