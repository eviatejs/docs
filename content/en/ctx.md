---
title: Context
description: ''
position: 3
category: API
---

We have moved on from `res` and `req` and have implemented ctx which has helper methods for returning `response` objects, and the data from incoming request.

# Methods

```ts
ctx.params
ctx.method
ctx.isSecure()
ctx.path
ctx.body
ctx.req //raw request object
ctx.url
ctx.headers
```

## c.params

```ts

// get single params 
app.get("/user/:name", (ctx:Context):EviateResponse => {
    return {
        text: `userName: ${ctx.params.name}`
    }
})


app.get("/")