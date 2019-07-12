## `setState()` 中的参数异步执行

`React.Component` 中这个方法接收两个参数，第一个是一个异步执行的函数

所以，下面的这个方法会报错 `TypeError: Cannot read property 'nodeValue' of null`，这时因为异步函数读取不到 `e: React.ChangeEvent` 这个变量

```js
// 注释部分的代码为正确代码
handleChange = (e: React.ChangeEvent) => {
    // const { nodeValue: value } = e.target;

    this.setState(() => (
        // { value }
        { value: e.target.nodeValue }
    ));
  };
```

解决办法是，先从事件对象中获取值，直接传递给异步函数（如注释部分代码所示）

## `setState()` 中的函数异步执行的特性，在结合`ref` 使用时，更容易出现 bug

```js

handleBtnClick() {
  this.setState(
    (prevState) => ({
      todo: [...prevState.todo, prevState.value],
      value: ''
    }),
    () => {
      return this.ul.querySelectAll('div').length;
    }
  );
}

```

上面是 `setState()` 和 `ref` 结合使用的正确姿势，如果把第二个函数的业务逻辑放在 `setState()` 方法后面执行，执行结果比实际值总是少一个，这个 bug 就是由于 `setState()` 异步执行的特性造成的