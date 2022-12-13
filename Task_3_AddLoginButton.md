# Add a log in button.

### Create the Component

- Create a `LoginButtonComponent` under the `src/components/` directory using the Angular CLI: `ng g component components/login-button`
- Inject the `AuthService` from the `@auth/auth0-angular` SDK.
- Create a `loginWithRedirect` Function inside the `LoginButtonComponent` and call the `loginWithRedirect` Function on the `AuthService`

### Populate the template file

- add a Button-HTML Tag (you can add the CSS-Class `btn btn-primary btn-block` to get some styling as well)
- Add a `click` Event handler for the Button an call your `loginWithRedirect()` Function inside of it.

### Update the NavBarComponent

- Inside the Template Add the `app-login-button`-Tag beneath the `app-main-nav` (to get some styling you can also wrap the `app-login-button` Tag inside a `div` and apply CSS class `navbar-nav ml-auto`)
- The `LoginButton` should be displayed whenever an user isn't authenticated yet, to get this information we need to inject the `AuthService` into the `NavBarComponent` as well.
- The `AuthService` has a property `isAuthenticated$` which holds an Observable with the information if the user is already authenticated.
- Use the structual directive `ngIf` and subscribe to this Observable using the `AsyncPipe` inside the `<app-login-button>`
- As soon as you applied everything the `LoginButton` should be hidden after you have successfuly authenticated yourself with Auth0.

### Hints

```javascript
// src/app/components/login-button/login-button.component.ts

import { Component, OnInit } from '@angular/core';
import { AuthService } from '@auth0/auth0-angular';

@Component({...})
export class LoginButtonComponent implements OnInit {
  constructor(private readonly auth: AuthService) {}

  loginWithRedirect(): void {
    this.auth.loginWithRedirect();
  }
}
```

```html
<!-- src/app/components/login-button/login-button.component.html -->
<button class="btn btn-primary btn-block" (click)="loginWithRedirect()">
  Log in
</button>

// src/app/components/nav-bar/nav-bar.component.html
<app-main-nav></app-main-nav>
<div class="navbar-nav ml-auto">
    <app-login-button
            *ngIf="(auth.isAuthenticated$ | async) === false">
    </app-login-button>
</div>
```
