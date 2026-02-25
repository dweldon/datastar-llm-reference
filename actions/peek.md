# `@peek()`

Accesses signal values without triggering re-evaluation when those signals change.

## Signature

```
@peek(callable: () => any)
```

The expression containing `@peek()` will **not** re-evaluate when signals accessed inside the callback change, though their current values are still readable.

## Example

```html
<!-- Only re-evaluates when $foo changes, not when $bar changes -->
<div data-text="$foo + @peek(() => $bar)"></div>
```
