## vue3 + vite + eslint

### 安装 vue3 项目

vite 支持的模板预设包括：

- vanilla
- vanilla-ts
- vue
- vue-ts
- react
- react-ts
- preact
- preact-ts
- lit-element
- lit-element-ts
- svelte
- svelte-ts

```
// 安装 vue3
yarn create vite admin --template vue

// 启动项目
yarn dev
```

### 添加 eslint 支持

安装 eslint

引入规则 Airbnb 规则 添加 eslint 官方 vue 插件

```
yarn add eslint eslint-plugin-vue eslint-config-airbnb-base -D
```

#### 创建 .eslintrc.js 文件

```
module.exports = {
  root: true,
  env: {
    browser: true,
    es2021: true,
  },
  parserOptions: {
    ecmaVersion: 12,
  },
  extends: [
    'plugin:vue/vue3-recommended',
    'airbnb-base'
  ]
}
```

### 添加 prettier 支持

```
yarn add prettier -D
yarn add eslint-plugin-prettier -D
```

修改 .eslintrc.js

```
...
plugins: ['prettier'],
rules: {
  'prettier/prettier': 'error',
}
...
```

配置完后， eslint 和 prettier 如果发生规则冲突，这时候就需要另一个 eslint 的插件 eslint-config-prettier，把 eslint 所有格式相关的校验都交给 prettier 处理。

```
yarn add eslint-config-prettier -D
```

修改 .eslintrc.js

```
...
plugins: ['prettier'],
extends: [
  'plugin:vue/vue3-recommended',
  'airbnb-base',
  // extends 中后引入的规则会覆盖前面的规则
  'plugin:prettier/recommended',
],
rules: {
  'prettier/prettier': 'error',
}
...
```

创建 .prettierrc.js

```
module.exports = {
  singleQuote: true, // 使用单引号
}
```
