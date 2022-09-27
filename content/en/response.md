---
title: Response
description: ''
position: 3
category: API
---

Response is what makes eviate so special, instead of having a response object with methods to handle responses, we have made it so that you can just return a response object and rest of the executions would be handled internally

## Interface 

```ts
export interface EviateResponse {
  status?: number;
  text?: string;
  json?: { [key: string]: any };
  error?: Error | string | { [key: string]: any };
  headers?: { [key: string]: string };
  interface?: any;
  Blob?: Blob;
}
```

### Note

**You could either send a text feild or json response when returning the response object**

## Basic response

```ts
app.get("/", (ctx:Context):EviateResponse => {
    return {
        text: "Hello World"
        status: 200,
    }
})
```

## Interface response

We have added an interface field which takes any Blob as input so you can handle files, audio or whatever you want through interface field

```ts
app.get("/", (ctx:Context):EviateResponse => {
    return {
        interface: ctx.file("./send.png")
        status: 200,
    }
})
```
