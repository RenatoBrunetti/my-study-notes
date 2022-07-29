# Liskov Substitution Principle - LSP
[main](../../../README.md) | [software-development-principles](../../README.md) | [solid](../README.md) | [liskov-substitution-principle](README.md)

## Description
Let q(x) be a property provable about objects of x of type T. Then q(y) should be provable for objects y of type S where S is a subtype of T.

> All this is stating is that every subclass/derived class should be substitutable for their base/parent class.

---

## Examples

### ✅ Correct implementation.
```typescript
// Person.ts

export default abstract class Person {
  sayHello(): void {}
}
```

```typescript
// Brazilian.ts

export default class Brazilian extends Person {
  sayHello(): void {
    console.log('Olá')
  }
}
```

```typescript
// American.ts

export default class American extends Person {
  sayHello(): void {
    console.log('Hello')
  }
}
```

```typescript
// SayHelloInPortuguese.ts

export default class SayHelloInPortuguese {
  sayOla(pessoa: Brazilian): void {
    pessoa.sayHello()
  }
}
```

```typescript
// index.ts

import { Brazilian } from './Brazilian.ts';
import { American } from './American.ts';
import { SayHelloInPortuguese } from './SayHelloInPortuguese.ts';

const brazilian = new Brazilian();
brazilian.sayHello()

const american = new American();
american.sayHello()

const brazilianHello = new SayHelloInPortuguese();
brazilianHello.sayOla(brazilian);
```
