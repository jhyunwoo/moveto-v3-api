```txt
npm install
npm run dev
```

```txt
npm run deploy
```

[For generating/synchronizing types based on your Worker configuration run](https://developers.cloudflare.com/workers/wrangler/commands/#types):

```txt
npm run cf-typegen
```

Pass the `CloudflareBindings` as generics when instantiation `Hono`:

```ts
// src/index.ts
const app = new Hono<{ Bindings: CloudflareBindings }>()
```

## Project context and engineering approach

This repository is an experimental third-generation API surface for Moveto. It tests a lightweight Cloudflare Workers architecture before product behavior and persistence concerns are committed to a larger service.

Hono supplies the HTTP interface and Wrangler supplies local development, deployment, and generated binding types. Keeping Worker bindings in generated TypeScript avoids configuration-only values leaking into untyped request code.

## Technology

- Cloudflare Workers and Wrangler for serverless execution
- Hono for the HTTP application layer
- TypeScript and generated binding definitions for configuration safety

## Status

Prototype API repository and deletion-review candidate; no production service is represented here.
