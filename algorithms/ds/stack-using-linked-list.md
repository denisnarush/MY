# Stack using linked list

## Interface

```typescript
type TUnitData<Type> = {
  [Property in keyof Type]: Type[Property];
};
```

## Unit class

```typescript
class Unit<Type> {
  data: TUnitData<Type>;
  next: Unit<Type> | undefined;

  constructor(data: TUnitData<Type>) {
    this.data = data;
  }
}
```

## Main class

```typescript
class Stack<Type> {
  private top: Unit<Type> | undefined;

  isEmpty(): boolean {
    return this.top == null;
  }

  peek(): TUnitData<Type> | undefined {
    return this.top?.data;
  }

  push(value: TUnitData<Type>): void {
    const node = new Unit(value);
    node.next = this.top;
    this.top = node;
  }

  pop(): TUnitData<Type> | undefined {
    const data = this.top?.data;
    this.top = this.top?.next;
    return data;
  }
}
```

## Test

```typescript
interface ITest {
  url: string;
}

const stack = new Stack<ITest>();
stack.isEmpty();
```
