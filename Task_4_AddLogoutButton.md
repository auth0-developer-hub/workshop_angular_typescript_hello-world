# Add a log out button

After we have successfully added a login button that hides after we authenticated ourselves. We also need a logout button for being able to logout as well.

### Create the Component

- Create a `LogoutButtonComponent` under the `src/shared/components/buttons/` directory using the Angular CLI: `ng g component shared/components/button/logout-button`
- Inject the `AuthService` from the `@auth/auth0-angular` SDK.
- Create a `handleLogout` Function inside the `LogoutButtonComponent` and call the `logout` Function on the `AuthService`
- Inside the `handleLogout` Function You pass it an optional configuration object to tell Auth0 where to take users after it logs them out: `{ returnTo: this.doc.location.origin }`
- For this you need to Inject the `Document` token from `@angular/common` as well.

### Populate the template file

- Add a Button-HTML Tag (you can add the CSS-Class `button__logout` to get some styling as well)
- Add a `click` Event handler for the Button an call your `handleLogout()` Function inside of it.

### Update tbe nav-bar
Again we need to update the `NavBarButtonsComponent` as well:

- Open the `NavBarButtonsComponent`: `src/app/shared/components/navigation/desktop/nav-bar-buttons.component.ts`
- Add the `app-logout-button` Tag right above the `app-login-button`
- You can either use the `NgIfElse`-Syntax here or add again another structural directive inside the `app-logout-button` to have this Button displayed as soon as the `isAuthenticated$`-Property returns true.

**As soon as you applied everything the `LogoutButton` should be shown up after you have successfuly authenticated yourself with Auth0.**

### Hints

```JavaScript
// src/shared/components/buttons/logout-button/logout-button.component.ts
@Component({
...
})
export class LogoutButtonComponent implements OnInit {
  constructor(
    public auth: AuthService,
    @Inject(DOCUMENT) private doc: Document
  ) {}

handleLogout(): void {
    this.auth.logout({ logoutParams: { returnTo: this.doc.location.origin } });
  }
}

```

```html
// src/shared/components/buttons/logout-button/logout-button.component.html
<button class="button__logout" (click)="handleLogout()">Log Out</button>
```

```html
// src/app/shared/components/navigation/desktop/nav-bar.component.html

<div class="nav-bar__buttons">
    <ng-container *ngIf="isAuthenticated$ | async; else loggedOut">
        <app-logout-button></app-logout-button>
    </ng-container>
    <ng-template #loggedOut>
        <app-login-button></app-login-button>
    </ng-template>
</div>
```
