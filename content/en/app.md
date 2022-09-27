---
title: Engine
description: ''
position: 3
category: API
---

Engine is the main constructor object exported by eviate

```ts
import { Engine } from "eviate"

const app: Engine = new Engine();

app.listen(); //automatically loads config from eviate.config.ts

```

<br>

## Engine Methods

These are the public `Engine` method: 

```ts
app.register(method, path, handler)
app.get(path, handler)
app.post(path, handler)
app.put(path, handler)
app.head(path, handler)
app.delete(path, handler)
app.patch(path, handler)
app.mount(router, path)
app.use(middleware, position)
app.on(event, callback)
app.error(callback)
app.listen(config?)
app.shutdown()
```

<br>

## Routing

Routing in eviate is similar to what other frameworks offer, tho we have different way of handling response check out `response`, for more info checkout `routing`


```ts
app.get("/hello-world", (ctx:Context):EviateResponse => {
    return {
        text: "Hello World",
        status: 200,
        headers: {}
    }
})
```

<br>

## Middlewares

Middlewares in eviate are functions which return `EviateMiddlewareResponse` which has `ctx` object which would be passed to next middleware for more check out `Middleware`

```ts
cors(ctx) => basicAuth(ctx) => logger(ctx)
```

<br>

## Listen

In Eviate engine automatically imports viable configs like port, hostname from `eviate.config.ts`, but you can pass parameters directly to listen function

```ts

app.listen({
    port: 3000,
    hostname: "localhost"
})

app.listen() //imports from config file onload
```