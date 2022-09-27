---
title: Introduction
description: ''
position: 1
category: ''
features:
  - Feature 1
  - Feature 2
  - Feature 3
---

Eviate is a javascript backend web framework aiming to be the goto option of next-gen builders, and change the way backend in javascript is structured. Eviate is even smaller than 5kb compared to other frameworks like express (210 kb), nestjs (100kb) and koajs (110kb).
# Why eviate?

We're hard at work to build a fresh new (well, another) web framework, but I promise it's different this time.

## What's the problem?

Currently, web frameworks in Javascript always use the same syntax and features all over, nothing has changed so
far. We're not saying that this is bad, but we think that there's a lot of room for improvement.

To point out the issues, here are something that we think are wrong with the current state of web frameworks:

- **User-friendly API**: All the current web frameworks have a very similar API, and it's not very user-friendly.
  They claim it's user friendly, and it quite is in the starting, but as you dive deeper, you'll find that it
  gets quite a bit harder to use. We want to make it easier to use, and we want to make it easier to learn.

- **Performance**: This is the **biggest** selling point being used by all frameworks. Every new framework
  claims to be the fastest, and they all have their own way of doing it. We had to do it anyways, but not with
  first proprity on maximum requests, but rather utilizing bun, the fastest JS runtime as of now, aswell optimized
  and simple syntax to deliver the best performance possible with low overhead.

- **Features** - We understand that, more code requires more overhead and we totally respect that. Hence, that's
  why we split the codebase into multiple modules, and even a lot of the features as plugins, so that you can
  choose what you want to use, and what you don't want to use. We want to make it as simple as possible.

- **Plugin API** - It's 2022, and we see every other framework using an old school plugin API. We have built
  something that you're definitely going to love, making you ship all the cool plugin ideas you've got 😎

## How are we next gen?

Here are some of the coolest stuff we've been shipping recently:

- **No more `req` or `res`**: Yes! this is the biggest one we're proud of. Finally, we've replaced `req` and `res`
  with context (`ctx`) to get data enough for you to get the request data. To make it simpler, the `res.send` or
  `res.json` or response returning is much more simpler. No more methods, return an object and we automagically
  convert it to the response you need.

- **First-class event handlers**: Event handlers a must to have fine-grained control over your app, and we
  understand that from out experience. We're providing you to register event handlers to control all kind of stuff
  going all over the app, eg. when your app starts, shuts down, pre-request, post-request, etc.

- **Global error handler**: It's super super tiring to add `try-catch` everywhere isn't it? We have converted raising
  errors to rather streaming them into a function where you can handle each of them peacefully.

- **First-class type-safe state**: It's super important to hold states such as your database connection, etc and
  it's even important for them to be type-safe. We've made it possible to hold states in a type-safe manner, and
  even access them from anywhere in your app.

- **URL redirection**: We realize remembering every type of route is actually hectic, like so much. So, we decided to
  simplify it. Here's how:

```ts
// There's 2 routes, `/home` and `/api/home` (namespaced under router called `api`).

// Redirect to home
return {
  redirect: app.url_for('home')
};

// Redirect to api home
return {
  redirect: app.url_for('api.home')
};

// You can even attach dynamic parameters
// eg. if your URL is `/hello/:num/profile/:name`
return {
  redirect: app.url_for('api.home', { num: 10, name: 'eviate' })
};
```

- **Flexible middlewares**: Using the new context pattern, we've adapted them to follow it. With no more `next`
  function, just modify and return context or a response, easy as that. To make it even better, middlewares can
  be now, pre-request, or post-request and will be called based on that.