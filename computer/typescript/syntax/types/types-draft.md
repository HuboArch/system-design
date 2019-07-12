## const and interface

```js
const student = {
  name: 'lily',
  age: 12
} 

// error
const student = {
  name: 'tom',
  age: 11
}
```

`cosnt` 方式声明的变量，引用不可变。但引用指向的对象可变 -> 如果想让对象的属性也不可变，使用 `interface` 的 `readonly`

总结：const -> interface{ readonly }