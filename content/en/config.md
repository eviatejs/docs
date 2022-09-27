---
title: Config
description: ''
position: 3
category: MISC
---

So each eviate app has a file name `eviate.config.ts/js` which is automatically imported internally and acts as a center point of config


## Config Object

```ts
 interface config {
  port: number;
  hostname: string;
  debug: boolean;
  state?: Record<string, any>;
  startMiddlewares?: MiddlewareHandler[];
  endMiddlewares?: MiddlewareHandler[];
  routers?: Router[];
  plugins?: Plugin[];
}
```

## Env

We autmatically load your `.env` files no need to do `require("dotenv").config()`

```ts
console.log(process.env.PORT) //this automatically configured without any setup
```