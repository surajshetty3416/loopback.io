---
lang: en
title: 'API docs: express.middleware'
keywords: LoopBack 4.0, LoopBack 4, Node.js, TypeScript, OpenAPI
sidebar: lb4_sidebar
editurl: https://github.com/strongloop/loopback-next/tree/master/packages/express
permalink: /doc/en/lb4/apidocs.express.middleware.html
---

<!-- Do not edit this file. It is automatically generated by API Documenter. -->

[Home](./index.md) &gt; [@loopback/express](./express.md) &gt; [Middleware](./express.middleware.md)

## Middleware interface

Interface LoopBack 4 middleware to be executed within sequence of actions. A middleware for LoopBack is basically a generic interceptor that uses `RequestContext`<!-- -->.

The signature of a middleware function is described at [Middleware](https://loopback.io/doc/en/lb4/apidocs.express.middleware.html)<!-- -->. It's very much the same as [Koa middleware](https://github.com/koajs/koa/blob/master/docs/guide.md#writing-middleware)<!-- -->.

<b>Signature:</b>

```typescript
export interface Middleware extends GenericInterceptor<MiddlewareContext> 
```
<b>Extends:</b> [GenericInterceptor](./context.genericinterceptor.md)<!-- -->&lt;[MiddlewareContext](./express.middlewarecontext.md)<!-- -->&gt;

## Example


```ts
const log: Middleware = async (requestCtx, next) => {
  const {request} = requestCtx;
  console.log('Request: %s %s', request.method, request.originalUrl);
  try {
    // Proceed with next middleware
    await next();
    console.log('Response received for %s %s', request.method, request.originalUrl);
  } catch(err) {
    console.error('Error received for %s %s', request.method, request.originalUrl);
    throw err;
  }
}

```


