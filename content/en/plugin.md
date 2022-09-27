---
title: Setup
description: ''
position: 4
category: PLUGIN
---


## Introduction

Plugins are basically extra layer to your eviatejs app they can add routes, middlewares and much more, they are added externally through `app.plugin` methods or mentioning them in your `eviate.config.ts` file. They run internally when you call `app.plugin.run()` method.


## Setup 

You can generate plugin based boiler plate app through `create-eviate-app` 


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

or You can add them through your package manager and set them up manually 


<code-group>
  <code-block label="Yarn" active>

  ```bash
  yarn add @eviatejs/plugin --save
  ```

  </code-block>
  
  <code-block label="NPM">

  ```bash
  npm install @eviatejs/plugin --save
  ```

  </code-block>
  <code-block label="PNPM">

  ```bash
  pnpm install @eviatejs/plugin --save
  ```

  </code-block>
</code-group>

## Create your own plugins

`@eviatejs/plugin` exports a default abstract class which you can extend 

```ts
export abstract class Plugin {
  public readonly event: EventEmitter;

  private _metadata: AppMetadata;

  constructor(metadata: AppMetadata) {
    this._metadata = { ...defaultAppMetadataValue, ...metadata };

    this.event = new EventEmitter();
  }

  public get metadata(): AppMetadata {
    return this._metadata;
  }

  public abstract handler(app: Engine): void;

  abstract get settings(): PluginSettings;
}
```

The abstract method handler is where your main logic of plugin needs to be, it runs internally and is passed the param `app` which is an instance of `Engine`


```ts

app.plugin.run() //this would run handler method internally in all plugins

```

