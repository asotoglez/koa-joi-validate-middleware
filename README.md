# Koa Joi Validate Middleware
![](https://img.shields.io/npm/dm/koa-joi-validate-middleware.png?style=flat-square)
**Validate middleware generator using *Joi***

Easily create [Koa](https://github.com/koajs/koa) middleware for validate with [Joi](https://github.com/hapijs/joi).

​

## Install

```shell
$ npm i koa-joi-validate-middleware
```

​

## Usage

### Import

```js
const validateMiddleware = require('koa-joi-validate-middleware');
```

​

### Create Validate Middleware

```js
const schema = {
  // Request headers Joi validation object
  headers: Joi.object({
  }),

  // URL query string Joi validation object
  query: Joi.object({
  }),

  // URL path parameters Joi validation object
  params: Joi.object({
    id: Joi.string().required(),
  }).required(),

  // POST body Joi validation object
  body: Joi.object({
  }),
};

const validator = validateMiddleware.create(schema, errorCallback);
```

#### errorCallback

```js
function errorCallback(ctx, error) {
}
```

​

### Use Validate Middleware

```js
router.get('/user', validator, async (ctx) => {
  const { id } = ctx.params;
  const response = await getUserInfo(id);
  ctx.body = response;
});

```

