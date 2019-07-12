## Function Types

Interfaces are capable of describing function types

to describe a function type with an interface, we **give the interface a call signature**

```typescript
interface SearchFunc {
  (src: string, subStr: string): number
}

let mySearch: SearchFunc

mySearch = (src, sub) => src.search(sub)
```

## Indexable Types

to describe a function type with an interface, we **give the interface a index signature**

```typescript
interface StringArray {
  [idx: number]: string
}

let myArray: StringArray = ['dean', 'sammy']
```

## 知识点类比：function types vs indexable types

这两个类型定义相似，类型对象的调用形式也差不多

```typescript
mySearch("abc", "bc");

myArray[0];
```
