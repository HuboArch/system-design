## destructure of function parameter

```typescript
interface SquareConfig {
  color: string
  width?: number  // optional -> destructure param with default value
}

const area = ({color,width = 10}) => `a ${color} square with ${width * width} area.`
```

## spread and default option bag

```typescript
const defaultConfig = {
  count: 10,
  delta: 1
}

let customConfig = {...defaultConfig, delta: 2}
```

## interface -> mixed type

```typescript
interface Counter {
  (start: number): string

  interval: number
  
  reset():void
}

function getCounter(): Counter {
  let counter = ((start) => `start time : ${start}`) as Counter

  counter.interval = 5.0

  counter.reset = () => {console.log('reset counter')}

  return counter
}
```


