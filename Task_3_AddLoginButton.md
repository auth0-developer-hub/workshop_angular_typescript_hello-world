# Add a log in button.

### Create the Component

- Create a `LoginButtonComponent` under the `src/shared/components/buttons/` directory using the Angular CLI: `ng g component shared/components/button/login-button`
- Inject the `AuthService` from the `@auth/auth0-angular` SDK.
- Create a `handleLogin` Function inside the `LoginButtonComponent` and call the `loginWithRedirect` Function on the `AuthService`

### Populate the template file

- add a Button-HTML Tag (you can add the CSS-Class `button__login` to get some styling as well)
- Add a `click` Event handler for the Button an call your `handleLogin()` Function inside of it.

### Update the NavBarButtonsComponent

- Open the `NavBarButtonsComponent`: `src/app/shared/components/navigation/desktop/nav-bar-buttons.component.ts`
- Inside the Template Add the `app-login-button`-Tag between the `div`-Tag
- The `LoginButton` should be displayed whenever an user isn't authenticated yet, to get this information we need to inject the `AuthService` into the `NavBarButtonComponent` as well.
- The `AuthService` has a property `isAuthenticated$` which holds an Observable with the information if the user is already authenticated.
- Use the structural directive `ngIf` and subscribe to this Observable using the `AsyncPipe` inside the `<app-login-button>`

**As soon as you applied everything the `LoginButton` should be hidden after you have successfuly authenticated yourself with Auth0.**

### Hints

```javascript
// src/app/shared/components/buttons/login-button/login-button.component.ts

import { Component, OnInit } from '@angular/core';
import { AuthService } from '@auth0/auth0-angular';

@Component({...})
export class LoginButtonComponent implements OnInit {
  constructor(private readonly auth: AuthService) {}

handleLogin(): void {
    this.auth.loginWithRedirect();
  }
}
```

```html
<!-- src/app/components/login-button/login-button.component.html -->
<button class="button__login" (click)="handleLogin()">
  Log in
</button>

<!-- src/app/shared/components/navigation/desktop/nav-bar-buttons.component.html
<div class="nav-bar__buttons">
    <app-login-button
            *ngIf="(isAuthenticated$ | async) === false">
    </app-login-button>
</div>
```
