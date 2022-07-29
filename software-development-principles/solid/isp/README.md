# Interface Segregation Principle - ISP
[main](../../../README.md) | [software-development-principles](../../README.md) | [solid](../README.md) | [interface-segregation-principle](README.md)

## Description
A client should never be forced to implement an interface that it doesn’t use or clients shouldn’t be forced to depend on methods they do not use.

---

## Examples

### ✅ Correct implementation.
```typescript
// Interfaces.ts

export interface PrinterInterface {
  print(): void
}

export interface CopyMachineInterface {
  copy(): void
}

export interface StaplerInterface {
  staple(): void
}
```

```typescript
// SimplePrinter.ts

import { PrinterInterface } from './PrinterInterface.ts';

export default class SimplePrinter implements PrinterInterface {
  print(): void {
    console.log('Simple - Printing!!!')
  }
}
```

```typescript
// MultiFunctionPrinter.ts

import { PrinterInterface } from './PrinterInterface.ts';
import { CopyMachineInterface } from './CopyMachineInterface.ts';

export default class MultiFunctionPrinter implements PrinterInterface, CopyMachineInterface {
  print(): void {
    console.log('Multi - Printing!!!')
  }
  copy(): void {
    console.log('Multi - Copying!!!')
  }
}
```

```typescript
// SuperMultiFunctionPrinter.ts

import { PrinterInterface } from './PrinterInterface.ts';
import { CopyMachineInterface } from './CopyMachineInterface.ts';
import { StaplerInterface } from './StaplerInterface.ts';

export default class SuperMultiFunctionPrinter implements PrinterInterface, CopyMachineInterface, StaplerInterface {
  print(): void {
    console.log('Super - Printing!!!')
  }
  copy(): void {
    console.log('Super - Copying!!!')
  }
  staple(): void {
    console.log('Super - Stapling!!!')
  }
}
```

```typescript
// index.ts

import { SimplePrinter } from './SimplePrinter.ts';
import { MultiFunctionPrinter } from './MultiFunctionPrinter.ts';
import { SuperMultiFunctionPrinter } from './SuperMultiFunctionPrinter.ts';

const simplePrinter = new SimplePrinter();
simplePrinter.print();

const multiFunctionPrinter = new MultiFunctionPrinter();
multiFunctionPrinter.print();
multiFunctionPrinter.copy();

const superMultiFunctionPrinter = new SuperMultiFunctionPrinter();
superMultiFunctionPrinter.print();
superMultiFunctionPrinter.copy();
superMultiFunctionPrinter.staple();
```

---

### ❌ Wrong implementation.
This implementation violates the interface segregation principle because the class **SimplePrinter** that implements **PrinterInterface** just uses the **print** method instead using all of the methods.

```typescript
// Interfaces.ts

export interface PrinterInterface {
  print(): void
  copy(): void
  staple(): void
}
```

```typescript
// SimplePrinter.ts

import { PrinterInterface } from './PrinterInterface.ts';

export default class SimplePrinter implements PrinterInterface {
  print(): void {
    console.log('Simple - Printing!!!')
  }
}
```
