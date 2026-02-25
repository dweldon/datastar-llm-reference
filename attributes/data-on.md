# `data-on`

Binds an event listener to an element, executing an expression when the event fires. The `evt` variable provides access to the event object.

## Syntax

```html
<button data-on:click="$foo = ''">Reset</button>
<div data-on:my-event="$foo = evt.detail"></div>
```

## Modifiers

| Modifier | Effect |
|----------|--------|
| `__once` | Executes only once |
| `__passive` | Prevents calling `preventDefault` |
| `__capture` | Uses capture phase |
| `__prevent` | Calls `preventDefault` |
| `__stop` | Calls `stopPropagation` |
| `__window` | Attaches listener to `window` |
| `__outside` | Triggers when event occurs outside the element |
| `__case.camel` / `.kebab` / `.snake` / `.pascal` | Converts event name casing |
| `__delay.Nms` / `__delay.Ns` | Delays execution |
| `__debounce.Nms` | Debounces; sub-modifiers: `.leading`, `.notrailing` |
| `__throttle.Nms` | Throttles; sub-modifiers: `.noleading`, `.trailing` |
| `__viewtransition` | Wraps in `document.startViewTransition()` |

## Example

```html
<input data-signals:query="''"
       data-on:input__debounce.300ms="$query = evt.target.value" />

<button data-on:click__once="@post('/api/init')">Initialize</button>

<div data-on:keydown__window="$key = evt.key"></div>
```
