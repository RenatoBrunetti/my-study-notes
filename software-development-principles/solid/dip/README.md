# Dependency Inversion Principle - ISP
[main](../../../README.md) | [software-development-principles](../../README.md) | [solid](../README.md) | [dependency-inversion-principle](README.md)

## Description
Entities must depend on abstractions not on concretions. It states that the high level module must not depend on the low level module, but they should depend on abstractions.

---

## Examples

### ✅ Correct implementation.
```typescript
// Interfaces.ts

export interface EmailInterface {
  address: string
  subject: string
  body: string
}

export interface EmailServiceInterface {
  sendMail(email: EmailInterface): void
}
```

```typescript
// FakeEmailService

import { EmailInterface } from './EmailInterface.ts';

export default class FakeEmailService {
  sendMail(email: EmailInterface): void {
    console.log('Sending email...', email)
  }
}
```

```typescript
// EmailNotification.ts

import { EmailInterface } from './EmailInterface.ts';
import { EmailServiceInterface } from './EmailServiceInterface.ts';

export default class EmailNotification {

  private emailService: EmailServiceInterface;

  constructor(emailService: EmailServiceInterface) {
    this.emailService = emailService;
  }

  public sendEmail(email: EmailInterface): void {
    this.emailService.sendMail(email)
  }
}
```

```typescript
// index.ts

import { FakeEmailService } from './FakeEmailService.ts';
import { EmailNotification } from './SimplePrinter.ts';

const fakeEmailService = new FakeEmailService();

const emailNotification = new EmailNotification(fakeEmailService);

const email = {
  address: 'john.sample@js.com',
  subject: 'Check this out',
  body: 'If you are looking for something special, you just found!'
};

emailNotification.sendEmail(email);
```

---

### ❌ First wrong implementation.
This implementation violates the dependency inversion principle because the **emailService** constant inside the **EmailNotification** class is referencing a concretion implementation.

```typescript
// EmailNotification.ts

export default class EmailNotification {

  private emailService: StaticEmailService; // Concretion implementation

  constructor(emailService: StaticEmailService) { // Concretion implementation
    this.emailService = emailService;
  }

  public sendEmail(email: EmailInterface): void {
    this.emailService.sendMail(email)
  }
}
```

---

### ❌ Second wrong implementation.
This implementation violates the dependency inversion principle because it implements a concretion implementation for **StaticEmailService** in **EmailNotification** class.

```typescript
// EmailNotification.ts

import { StaticEmailService } from '../../wherever/StaticEmailService.ts'; // Concretion implementation

export default class EmailNotification {

  private emailService: StaticEmailService = new StaticEmailService(); // Concretion implementation

  constructor() {
  }

  public sendEmail(email: EmailInterface): void {
    this.emailService.sendMail(email)
  }
}
```
