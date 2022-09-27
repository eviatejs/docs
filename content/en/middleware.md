---
title: Middleware
description: ''
position: 3
category: API
---


Middlewares in engine are functions which return `EviateMiddlewareResponse` which has `ctx` object which would be passed to next middleware for more check out `Middleware`

```ts
cors(ctx) => basicAuth(ctx) => logger(ctx)
```


## EviateMiddlewareResponse

You can upgrade and extend the old context and EviateMiddlewareResponse

```ts
export interface EviateMiddlewareResponse {
  status?: number;
  header?: { [key: string]: string };
  ctx: Context;
}
```

## Position

You can set middleware positions of their execution

```ts
app.use("before", middleware) // runs middleware pre-response

app.use("after", middlware) //runs after response is sent
```