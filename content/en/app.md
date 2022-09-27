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

# Engine Methods

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

# Routing

Routing in eviate is similar to what other frameworks offer, tho we have different way of handling response check out `response`



### Simple Handler

```ts
app.get("/", (ctx: Context):EviateResponse => {
    return {
        text: "Hello World",
        status: 200
    }
})
```

### Wild Card

```ts
app.get("/abc/*/wildcard", (ctx: Context):EviateResponse => {
    return {
        text: "Wild Card method",
        status: 200
    }
})
```

### Route Params 

```ts 
app.get("/route/:param", (ctx: Context):EviateResponse => {
    return {
        text: `${ctx.param.param} - Param`,
        status: 200
    }
})
```
Multiple params at once 

```ts
app.get("/user/:name/book/:data", (ctx: Context):EviateResponse => {
    const { name, data } = ctx.param
    return {
        text: `Book name is ${name} relased on ${date}`,
        status: 200
    }
})
```



