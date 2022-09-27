---
title: Router
description: ''
position: 3
category: API
---

The internal router in eviatejs is based on `radix tree` which is the best and most performant router out there, the exported router is based on caching of routes so that it won't give a heavy toll when appending all the routes from router to main `Engine` instance.

```ts
import {Router} from "eviate"

const router: Router = new Router()

export default router;
```

<br>

## Methods

```ts
app.register(method, path, handler)
app.get(path, handler)
app.post(path, handler)
app.put(path, handler)
app.head(path, handler)
app.delete(path, handler)
app.patch(path, handler)
app.getAllRoutes()
```

## Routing

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

## Mounting 

```ts

import { Engine, Router } from "eviate"

const app:Engine = new Engine();

const router:Router = new Router();

router.get("/router", (ctx:Context):EviateResponse => {
    return {
        json: {isRouter: true}
        status: 200,
        headers: {
            "Content-Type": "application/json"
        }
    }
})

app.mount(router, "/api" ) //Optional prefix for mounting of router
```