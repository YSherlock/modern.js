---
sidebar_label: enableFrameworkExt
---
# server.enableFrameworkExt

* 类型： `Boolean`
* 默认值： `false`

By default, with 【Custom Web Server](/docs/guides/advanced-features/web-server) enable, Middleware uses the syntax of the Modern.js itself.

Enable `server.enableFrameworkExt` to use the syntax of framework extensions.

```typescript title="modern.config.ts"
export default defineConfig({
  server: {
    enableFrameworkExt: true,
  }
});
```

## Example

Default usage:

```ts title="server/index.ts"
import { Middleware } from '@modern-js/runtime/server';

export const middleware: Middleware = (ctx, next) => {
  console.log(ctx.request.url);
  next();
};
```

When enabled, Middleware types will be exported from other namespaces and can the syntax of framework extensions:

```ts title="server/index.ts"
import { SomeType } from '@modern-js/runtime/{frameworknName}';

export const middleware: SomeType = (...args) => {
  console.log(args[0].url);
  next();
};
```

:::note
The above code is pseudo-code, and the specific usage needs to refer to the corresponding framework extension.
:::