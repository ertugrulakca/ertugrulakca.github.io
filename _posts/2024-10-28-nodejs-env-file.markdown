---
layout: post
title:  "Environment Variables"
date:   2024-10-28 22:30:00 +0300
categories: nodejs
---

* On cloud side; you can use custom solutions for environment variables. For example, AWS Secrets Manager, Azure Key Vault, Google Cloud Secret Manager and more. These services keep your secret values. In local environment, We will keep values on `.env` file.

```shell
npm install dotenv
```

```js
require('dotenv').config();

console.log(process.env.DATABASE_URI); // DATABASE_URI is an example. you can use your custom key
```
