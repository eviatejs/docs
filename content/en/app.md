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
