## eslint-prettier-webpack-demo

工程化-> ESLint + Prettier + lint-staged 统一规范代码风格.

### 安装 prettier

```
yarn add prettier --dev
```

### 配合 eslint 检测代码

1. 安装 eslint

```
yarn add eslint-config-prettier --dev
```

2. 配置 .eslintrc.js：

```
{
  extends: ['prettier']
}
```

3. 使用 eslint 运行 prettier

```
yarn add eslint-plugin-prettier --dev
```

3. 继续配置 .eslintrc.js

```
{
  "plugins": ["prettier"],
  "rules": {
    "prettier/prettier": "error"
  }
}
```

### 配置命令

```
"format": "onchange './*.js' 'src/**/*.js' 'static/**/*.html' 'static/**/*.js' -- prettier --write {{changed}}"
```

### 配置 prettier

prettier 还可以很好的集成的项目中，利用 git 的 hooks 机制，在提交 commit 时自动调用 pretter 进行格式化。实现这一点，还需要 Huksy、pretty-quick 这两个工具。
[](https://prettier.io/docs/en/options.html)

### 代码提交格式化

```
yarn add pretty-quick husky --dev
```

在 package.json 中添加：

```
"husky": {
  "hooks": {
    "pre-commit": "pretty-quick --staged"
  }
}
```

### 配置 .prettierignore

```
public
dist
*.html
```
