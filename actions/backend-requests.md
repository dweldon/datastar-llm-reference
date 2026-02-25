# Backend Requests

`@get()`, `@post()`, `@put()`, `@patch()`, `@delete()` send HTTP requests via the Fetch API and process SSE responses. Signals are sent as query parameters (GET) or in the request body (others).

## Signatures

```
@get(uri: string, options?: object)
@post(uri: string, options?: object)
@put(uri: string, options?: object)
@patch(uri: string, options?: object)
@delete(uri: string, options?: object)
```

## Shared Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `contentType` | `string` | `'json'` | `'json'` or `'form'` |
| `filterSignals` | `object` | `{include: /.*/}` | `{ include: RegExp, exclude?: RegExp }` to control which signals are sent |
| `selector` | `string \| null` | `null` | Form selector when using `contentType: 'form'` |
| `headers` | `object` | `{}` | Custom HTTP headers |
| `openWhenHidden` | `boolean` | `false` (GET) / `true` (others) | Keep SSE connection open when page is hidden |
| `payload` | `object` | — | Override the fetch payload entirely |
| `retry` | `string` | `'auto'` | `'auto'`, `'error'`, `'always'`, or `'never'` |
| `retryInterval` | `number` | `1000` | Milliseconds between retries |
| `retryScaler` | `number` | `2` | Multiplier for exponential backoff |
| `retryMaxWaitMs` | `number` | `30000` | Maximum wait between retries (ms) |
| `retryMaxCount` | `number` | `10` | Maximum retry attempts |
| `requestCancellation` | `string \| AbortController` | `'auto'` | `'auto'`, `'disabled'`, or an `AbortController` |

## Request Cancellation

By default (`'auto'`), a new fetch on an element cancels any existing request on that same element. Requests on different elements run concurrently.

- `'auto'` — Cancels previous request on the same element
- `'disabled'` — Allows concurrent requests from the same element
- `AbortController` — Manual control over cancellation

## Response Handling

The server responds with SSE events. The Content-Type determines processing:

**`text/html`** — Patches the DOM.
- `datastar-selector` — CSS selector for the target element(s)
- `datastar-mode` — `outer` (default), `inner`, `remove`, `replace`, `prepend`, `append`, `before`, `after`
- `datastar-use-view-transition` — Enable the View Transition API

**`application/json`** — Patches signals (merges into signal store).
- `datastar-only-if-missing` — Only patch signals that don't already exist

**`text/javascript`** — Executes JavaScript.
- `datastar-script-attributes` — JSON string of attributes for the script element

## Events

All backend actions dispatch `datastar-fetch` CustomEvents on the element. Access via `evt.detail.type`:

| Event Type | Description |
|------------|-------------|
| `started` | Request initiated |
| `finished` | Request completed successfully |
| `error` | Request encountered an error |
| `retrying` | Request is being retried |
| `retries-failed` | All retry attempts exhausted |

## Example

```html
<div data-signals="{query: ''}">
  <input data-bind:query />
  <button data-on:click="@get('/api/search', {
    filterSignals: {include: /^query$/},
    headers: {'X-Csrf-Token': 'abc'}
  })">Search</button>

  <div data-on:datastar-fetch="
    evt.detail.type === 'error' && console.error('Request failed')
  "></div>
</div>
```
