# Linked list

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
class LinkedList<Type> {
  private head: Unit<Type> | undefined;

  isEmpty(): boolean {
    return this.head == null;
  }

  append(data: TUnitData<Type>): void {
    if (this.head == null) {
      this.head = new Unit(data);
      return;
    }
    let current = this.head;
    while (current.next != null) {
      current = current.next;
    }
    current.next = new Unit(data);
  }
  prepend(data: TUnitData<Type>): void {
    const newHead = new Unit(data);
    newHead.next = this.head;
    this.head = newHead;
  }
}
```

## Optional Methods

```typescript
  deleteWithTheValue(data: TUnitData<Type>): void {
    if (this.head == null) return;

    if (this.head.data === data) {
      this.head = this.head.next;
      return;
    }

    let current = this.head;
    while (current.next != null) {
      if (current.next.data === data) {
        current.next = current.next.next;
        return;
      }

      current = current.next;
    }
  }
```

## Test

```typescript
interface ITest {
  url: string;
}

const ll = new LinkedList<ITest>();
ll.append({ url: "https://mydomain.ru" });
```
