---
title: Events
description: ''
position: 3
category: MISC
---


Eviatejs `Engine` has inbuilt event listeners, we strongly support event based handlers


## Event Handlers


### Startup 

This event runs when server is starting up

```ts
app.on("startup", () => console.log("server starting up"))
```

### Shutdown 

This event runs when server is shutting up

```ts
app.on("shutdown", () => console.log("server shutting down"))
```

### Before Request 

This event runs when before the request is recieved and response is sent

```ts
app.on("before-request", () => console.log("running pre-request callback"))
```
### Plugin Load 

This event runs when a plugin is loaded up

```ts
app.on("pluginLoad", () => console.log("Loaded new plugin"))
```
### Error 

This event runs when a error is caught

```ts
app.on("error", (err, ctx?) => {
    console.log(err, ctx.path)
})
```

### Config load 

This event runs when conifg has been loaded

```ts
app.on("configLoad", () => console.log("config loaded"))
```