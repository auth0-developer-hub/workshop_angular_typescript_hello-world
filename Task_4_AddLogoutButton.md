# Add a log out button

After we have successfully added a login button that hides after we authenticated ourselves. We also need a logout button for being able to logout as well.

### Create the Component

- Create a `LogoutButtonComponent` under the `src/components/` directory using the Angular CLI: `ng g component components/logout-button`
- Inject the `AuthService` from the `@auth/auth0-angular` SDK.
- Create a `logout` Function inside the `LogoutButtonComponent` and call the `logout` Function on the `AuthService`
- Inside the `logout` Function You pass it an optional configuration object to tell Auth0 where to take users after it logs them out: `{ returnTo: this.doc.location.origin }`
- For this you need to Inject the `Document` token from `@angular/common` as well.

### Populate the template file

- Add a Button-HTML Tag (you can add the CSS-Class `btn btn-primary btn-block` to get some styling as well)
- Add a `click` Event handler for the Button an call your `logout()` Function inside of it.

### Update tbe nav-bar
Again we need to update the `NavBarComponent` as well:

- Add the `app-logout-button` Tag right beneath the `app-login-button`
- You can either use the `NgIfElse`-Syntax here or add again another structural directive inside the `app-logout-button` to have this Button displayed as soon as the `isAuthenticated$`-Property returns true.

**As soon as you applied everything the `LogoutButton` should be shown up after you have successfuly authenticated yourself with Auth0.**

### Hints

```JavaScript
// src/app/components/logout-button/logout-button.component.ts
@Component({
...
})
export class LogoutButtonComponent implements OnInit {
  constructor(
    public auth: AuthService,
    @Inject(DOCUMENT) private doc: Document
  ) {}

  logout(): void {
    this.auth.logout({ returnTo: this.doc.location.origin });
  }
}

```

```html
// src/app/components/logout-button/nav-bar.component.html

<div class="navbar-nav ml-auto">
  <app-login-button 
*ngIf="(auth.isAuthenticated$ | async) === false">
  </app-login-button>
  
  <app-logout-button 
*ngIf="auth.isAuthenticated$ | async">
  </app-logout-button>

</div>
```
