---
title: File-Router
description: ''
position: 4
category: PLUGIN
---


## Introduction

File router is basically a `nextjs` inspired plugin which crawls through directories and saves them as routes and middlewares


## Installation 

You can generate file router based boiler plate app through `create-eviate-app` 


<code-group>
  <code-block label="Yarn" active>

  ```bash
  yarn create eviate-app
  ```

  </code-block>
  
  <code-block label="NPM">

  ```bash
  npx create-eviate-app
  ```

  </code-block>
  <code-block label="PNPM">

  ```bash
  pnpm create eviate-app
  ```

  </code-block>
</code-group>

or You can add it through your package manager and set them up manually 


<code-group>
  <code-block label="Yarn" active>

  ```bash
  yarn add @eviatejs/plugin @eviatejs/plugin-filesystem-router --save
  ```

  </code-block>
  
  <code-block label="NPM">

  ```bash
  npm install @eviatejs/plugin @eviatejs/plugin-filesystem-router --save
  ```

  </code-block>
  <code-block label="PNPM">

  ```bash
  pnpm install @eviatejs/plugin @eviatejs/plugin-filesystem-router --save
  ```

  </code-block>
</code-group>

## Setup

Setting up `file-router` is really easy you just need to append it to plugin stack

```ts 
import { Engine } from "eviate"
import { FileSystemRouter } from "@evitejs/plugin-filesystem-router"

const app:Engine = new Engine();

const router = new FileSystemRouter({
  routerDir: '/src/routes',  //routes dir
  middlewareDir: '/src/middlewares', //middleware dir
  log: false
});

app.plugin.load(router)

app.plugin.run()

app.listen()

```

## How it works

So file router reads the routes dir and trims the path and gets a route path like `/user/[param].ts` then through regex it parses it to `/user/:param` and appends it to tree with specified method and handler

```dir
src/
  1.routes/
    1.user/
        1.[param].ts             // Ignored content
    2.hello-world.ts
  2.middlwares/          // Ignored directory
    1.middleware-1.ts
    2.middleware-2.ts
```


## Exports

Each file should export an object with handler 

### Routes Export

Each route file should export an object called route, with fields `method` and `run`

```ts
import { Context, EviateResponse } from 'eviate';

export const route = {
  method: 'GET',
  run: (ctx: Context): EviateResponse => {
    console.log(ctx.path);
    return {
      text: 'Hello World',
      status: 200
    };
  }
};
```

### Middlewares Export

Each route file should export an object called middleware, with fields `position` and `run`, you can ignore the name field.

```ts
import { Context, EviateMiddlewareResponse } from 'eviate';
export const middleware = {
  name: 'basicLogger',
  position: 'before',
  run: (ctx: Context): EviateMiddlewareResponse => {
    return {
      ctx: ctx
    };
  }
};
```