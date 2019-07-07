## indexable type

```typescript
// this is easy
interface IndexableType {
  [propName: string]: number
}

// I'm confusing, what the usage scenario of this definition
interface anotherIndexableType {
  [idx: string]: Animal
  [idx: number]: Dog
}
```
