# Babel 7

# Babel 的功能

We can use Babel to compile JS app code that uses ES2015+ syntax into code that works in current browers.

Actually, babel will do two things to achieve that goal

1. Transforming new JS syntax
2. Polyfilling missing features

# Babel 正常工作依赖 `plugins` 和 `presets`

特定语法规则的转化需要对应的 plugin，plugin 本质上是一个 JS 程序，我们可以自己实现。

官方已经提供了一些插件，比如，`@babel/plugin-transform-arrow-functions`

我们可以使用这个插件来将代码中的箭头函数转换为普通函数，命令行命令如下：

```shell
npx babel src --out-dir lib --plugins=@babel/plugin-transform-arrow-functions
```

至于 presets，它其实是一组预定义的 plugins（JS 那么多的新语法，要是一个个配置 plugin 的话，会很麻烦）

# Babel 的使用步骤

1）安装依赖模块

```shell
npm install --save-dev @babel/core @babel/cli @babel/preset-env

npm install --save-dev @babel/polyfill
```

2）工程根目录新建 Babel 的配置文件 `babel.config.js`

```js
const presets = [
  [
    "@babel/env",
    {
      targets: {
        edge: "17",
        firefox: "60",
        chrome: "67",
        safari: "11.1",
      },
      useBuiltIns: "usage",
    },
  ],
];

module.exports = { presets };
```

3）在命令行中执行代码转译命令

```shell
./node_modules/.bin/babel src --out-dir lib
```

> note: npm 版本大于 5.2.0 时，上面的命令可简写为 `npx babel src --out-dir lib`


到此 OK

但是由于我们没有指定转换规则，所以，转译后的代码和源代码是相同的

