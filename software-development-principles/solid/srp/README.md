# Single Responsibility Principle - SRP
[main](../../../README.md) | [software-development-principles](../../README.md) | [solid](../README.md) | [single-responsibility-principle](README.md)

## Description
A class should have one and only one reason to change, meaning that a class should only have one job.

---

## Examples

### ✅ Correct implementation.
```typescript
// Square.ts

type SquareSizeType = {
  width: number;
  height: number;
}

export default class Square {
  private width: number;
  private height: number;

  constructor(length: number) {
    this.width = length;
    this.height = length;
  }

  public getSize(): SquareSizeType {
    return { width: this.width, height: this.height };
  }

  public getMessage(): string {
    return `The size is ${JSON.stringify(this.getSize())}`;
  }
}
```

```typescript
// Email.ts

export default class Email {
  public send(message: string): void {
    console.log('Sending email...');
    console.log('Message:', message);
  }
}
```

```typescript
// index.ts

import Square from './Square.ts';
import Email from './Email.ts';

const email = new Email();

const littleSquare: Square = new Square(10);
email.send(littleSquare.getMessage())

const bigSquare: Square = new Square(100);
email.send(bigSquare.getMessage())
```

---

### ❌ Wrong implementation.
The **sendEmail** method shouldn't be inside the Square class because this violates the single responsibility principle.

```typescript
// Square.ts

type SquareSizeType = {
  width: number;
  height: number;
}

class Square {
  private width: number;
  private height: number;
  private message: string;

  constructor(length: number) {
    this.width = length;
    this.height = length;
    this.message = `The size is ${JSON.stringify(this.getSize())}`;
  }

  public getSize(): SquareSizeType {
    return { width: this.width, height: this.height };
  }

  public sendEmail(): void {
    console.log('Sending email...');
    console.log('Message:', this.message);
  }
}
```

```typescript
// index.ts

import Square from './Square.ts';

const littleSquare: Square = new Square(10);
littleSquare.sendEmail();
```
