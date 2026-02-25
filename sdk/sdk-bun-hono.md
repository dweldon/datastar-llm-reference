# Bun/Hono SDK

Server-side helpers for streaming Datastar SSE responses from a Hono app running on Bun.

## `datastar.stream(c, callback, options?)`

Creates an SSE streaming response and provides a `DatastarStreamingApi` instance to the callback.

```ts
import { datastar } from './datastar';

app.get('/api/stream', (c) => {
  return datastar.stream(c, async (dsa) => {
    await dsa.patchSignals({ signals: { count: 1 } });
    await dsa.patchElements({ elements: '<div id="output">Hello</div>' });
  });
});
```

### Options

| Option | Type | Description |
|--------|------|-------------|
| `heartbeatInterval` | `number` | Interval in ms between keep-alive heartbeat comments |

## `datastar.readSignals(c)`

Reads Datastar signals from the request. For `GET` requests, reads from the `datastar` query parameter. For other methods, reads from the JSON body.

Returns a discriminated union:

```ts
// Success
{ success: true, signals: JsonObject }

// Error
{ success: false, error: string }
```

```ts
app.post('/api/action', async (c) => {
  const result = await datastar.readSignals(c);
  if (!result.success) return c.text(result.error, 400);
  const { signals } = result;
  // use signals...
});
```

## `DatastarStreamingApi`

Instance provided to the `datastar.stream()` callback. All methods return `Promise<void>`.

### `patchSignals({ signals, options? })`

Sends a `datastar-patch-signals` SSE event to update client-side signals.

```ts
await dsa.patchSignals({
  signals: { count: 42, name: 'Dave' },
  options: {
    onlyIfMissing: true, // only set signals not already present
    eventId: 'evt-1',
    retryDuration: 1000,
  },
});
```

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `onlyIfMissing` | `boolean` | `false` | Only set signals that don't already exist on the client |
| `eventId` | `string` | — | SSE event ID |
| `retryDuration` | `number` | — | SSE retry interval in ms |

### `patchElements({ elements, options? })`

Sends a `datastar-patch-elements` SSE event to update DOM content.

```ts
await dsa.patchElements({
  elements: '<div id="output">Updated</div>',
  options: {
    mode: 'inner',
    selector: '#target',
    useViewTransition: true,
  },
});
```

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `mode` | `ElementPatchMode` | `'outer'` | How the element is patched into the DOM |
| `selector` | `string` | — | CSS selector for the target element |
| `useViewTransition` | `boolean` | `false` | Use the View Transition API |
| `namespace` | `'html' \| 'svg' \| 'mathml'` | `'html'` | XML namespace for the element |
| `eventId` | `string` | — | SSE event ID |
| `retryDuration` | `number` | — | SSE retry interval in ms |

### `ElementPatchMode`

| Mode | Effect |
|------|--------|
| `outer` | Replaces the target element and its contents (default) |
| `inner` | Replaces the target element's children |
| `replace` | Replaces the target element |
| `prepend` | Inserts before the target's first child |
| `append` | Inserts after the target's last child |
| `before` | Inserts before the target element |
| `after` | Inserts after the target element |
| `remove` | Removes the target element |

### `executeScript({ script, options? })`

Appends a `<script>` tag to the body via `patchElements`. By default, the script auto-removes itself after execution.

```ts
await dsa.executeScript({
  script: 'console.log("hello from server")',
  options: {
    autoRemove: false,   // keep the script tag in the DOM
    attributes: ['type="module"'],
  },
});
```

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `autoRemove` | `boolean` | `true` | Remove the script element after execution via `data-effect="el.remove()"` |
| `attributes` | `string[]` | `[]` | Additional attributes to add to the `<script>` tag |
| `eventId` | `string` | — | SSE event ID |
| `retryDuration` | `number` | — | SSE retry interval in ms |

### `heartbeat()`

Sends an SSE comment (`: heartbeat`) to keep the connection alive.

```ts
await dsa.heartbeat();
```

## Full Example

```ts
import { Hono } from 'hono';
import { datastar } from './datastar';

const app = new Hono();

app.get('/', (c) => {
  return c.html(`
    <html>
    <head>
      <script type="module" src="https://cdn.jsdelivr.net/npm/@starfederation/datastar"></script>
    </head>
    <body data-signals='{"count": 0}'>
      <button data-on:click="@post('/api/increment')">+1</button>
      <span id="count" data-text="$count"></span>
    </body>
    </html>
  `);
});

app.post('/api/increment', async (c) => {
  const result = await datastar.readSignals(c);
  if (!result.success) return c.text(result.error, 400);

  const count = (result.signals.count as number) + 1;

  return datastar.stream(c, async (dsa) => {
    await dsa.patchSignals({ signals: { count } });
    await dsa.patchElements({
      elements: `<span id="count">${count}</span>`,
    });
  });
});

export default app;
```
