# Datastar LLM Reference

Concise Markdown reference for [Datastar](https://data-star.dev) core attributes, actions, and the Bun/Hono server SDK.

## Attributes

| File                                                                     | Description                                         |
| ------------------------------------------------------------------------ | --------------------------------------------------- |
| [data-attr](attributes/data-attr.md)                                     | Set HTML attributes from expressions                |
| [data-bind](attributes/data-bind.md)                                     | Two-way data binding between signals and elements   |
| [data-class](attributes/data-class.md)                                   | Add/remove CSS classes from expressions             |
| [data-computed](attributes/data-computed.md)                             | Read-only computed signals                          |
| [data-effect](attributes/data-effect.md)                                 | Reactive side effects                               |
| [data-ignore](attributes/data-ignore.md)                                 | Skip element during DOM walking                     |
| [data-ignore-morph](attributes/data-ignore-morph.md)                     | Skip element during morph patches                   |
| [data-indicator](attributes/data-indicator.md)                           | Loading state signal for fetch requests             |
| [data-init](attributes/data-init.md)                                     | Run expression on initialization                    |
| [data-json-signals](attributes/data-json-signals.md)                     | Debug display of signals as JSON                    |
| [data-on](attributes/data-on.md)                                         | Bind event listeners                                |
| [data-on-intersect](attributes/data-on-intersect.md)                     | React to viewport intersection                      |
| [data-on-interval](attributes/data-on-interval.md)                       | Repeat expression on a timer                        |
| [data-on-signal-patch](attributes/data-on-signal-patch.md)               | React to any signal change                          |
| [data-on-signal-patch-filter](attributes/data-on-signal-patch-filter.md) | Filter which signals trigger `data-on-signal-patch` |
| [data-preserve-attr](attributes/data-preserve-attr.md)                   | Preserve attributes during morph                    |
| [data-ref](attributes/data-ref.md)                                       | Signal reference to a DOM element                   |
| [data-show](attributes/data-show.md)                                     | Show/hide element from expression                   |
| [data-signals](attributes/data-signals.md)                               | Declare and patch signals                           |
| [data-style](attributes/data-style.md)                                   | Set inline styles from expressions                  |
| [data-text](attributes/data-text.md)                                     | Bind text content to expression                     |

## Actions

| File                                            | Description                                                      |
| ----------------------------------------------- | ---------------------------------------------------------------- |
| [@peek()](actions/peek.md)                      | Read signals without triggering reactivity                       |
| [@setAll()](actions/set-all.md)                 | Set value of matching signals                                    |
| [@toggleAll()](actions/toggle-all.md)           | Toggle boolean value of matching signals                         |
| [Backend Requests](actions/backend-requests.md) | `@get`, `@post`, `@put`, `@patch`, `@delete` with shared options |

## Server SDK

| File                                | Description                                                     |
| ----------------------------------- | --------------------------------------------------------------- |
| [Bun/Hono SDK](sdk/sdk-bun-hono.md) | SSE streaming, signal reading, and DOM patching from the server |
