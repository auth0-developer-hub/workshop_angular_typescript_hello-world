# Display Profile Information

After we have successfully logged in we also want to update the `ProfileComponent` to have some Profile Information displayed.

### Update the ProfileComponent

- First we need to inject again the `AuthService` inside the `src/app/pages/profile/profile.component.ts`
- To receive User Information the `AuthService` provides an `user$`Observable we can subscribe to
- Now we want to display the User's profile picture, the username and the users email. We cat get this information from our `user$` Observable which hold the properties `email`, `picture` and `name`
- Enhance the Template to display this information (you can take a glance at the hints for how to structure the html)
- To see more what the `user` Object hold you can just display it's stringified version inside the template by using the `JSONPipe` for it.


```javascript
// src/app/pages/profile/profile.component.ts

@Component({...})
export class ProfileComponent {
    user$: Observable<User>;
  constructor(private readonly auth: AuthService) {
    this.user$ = auth.user$;
    }
}
```


```html
<!--src/app/pages/profile/profile.component.html-->

<div *ngIf="auth.user$ | async as user">
  <div class="row align-items-center profile-header">
    <div class="col-md-2 mb-3">
      <img
        [src]="user.picture"
        alt="User's profile picture"
        class="rounded-circle img-fluid profile-picture"
      />
    </div>
    <div class="col-md text-center text-md-left">
      <h2>{{ user.name }}</h2>
      <p class="lead text-muted">{{ user.email }}</p>
    </div>
  </div>

  <div class="row">
    <pre class="col-12 text-light bg-dark p-4">{{ user | json }}</pre>
  </div>
</div>
```
