# Open Closed Principle - OCP
[main](../../../README.md) | [software-development-principles](../../README.md) | [solid](../README.md) | [open-closed-principle](README.md)

## Description
Objects or entities should be open for extension, but closed for modification.

---

## Examples

### ✅ Correct implementation.
```typescript
// ShapeInterface.ts

export default class ShapeInterface {
  draw(): void {}
}
```

```typescript
// Circle.ts

export default class Circle extends ShapeInterface {
  draw(): void {
    console.log('⏺️');
  }
}
```

```typescript
// Triangle.ts

export default class Triangle extends ShapeInterface {
  draw(): void {
    console.log('🔼');
  }
}
```

```typescript
// index.ts

import { Circle } from './Circle.ts';
import { Triangle } from './Triangle.ts';

const littleCircle = new Circle();
littleCircle.draw();

const littleTriangle = new Triangle();
littleTriangle.draw();
```

---

### ❌ Wrong implementation.
This implementation violates the open/closed principle because it needs to change the **draw** method inside the **Shape** class to add a new **Square** shape. In other hand, the correct implementation just need to create a **Square** class that implements **ShapeInterface** like all the other classes.

```typescript
// Shape.ts

export default class Shape {
  private shape: string;

  constructor(shape: string) {
    this.shape = shape;
  }

  draw(): void {
    if(this.shape === 'circle'){
      console.log('⏺️');
    } else if(this.shape === 'triangle') {
      console.log('🔼');
    }
  }
}
```

```typescript
// index.ts

import { Shape } from './Shape.ts';

const firstCircle = new Shape('circle');
firstCircle.draw();

const firstTriangle = new Shape('triangle');
firstTriangle.draw();

const firstSquare = new Shape('square');
firstSquare.draw();
```
