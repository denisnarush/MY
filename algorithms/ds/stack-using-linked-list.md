# Stack using linked list
```typescript
class Unit {
  data: number;
  next: Unit | undefined;

  constructor(data: number) {
    this.data = data;
  }
}
```
```typescript
class Stack {
  private top: Unit | undefined;

  isEmpty(): boolean {
    return this.top == null;
  }

  peek(): number | undefined {
    return this.top?.data;
  }

  push(value: number): void {
    const node = new Unit(value);
    node.next = this.top;
    this.top = node;
  }

  pop(): number | undefined {
    const data = this.top?.data;
    this.top = this.top?.next;
    return data;
  }
}
```