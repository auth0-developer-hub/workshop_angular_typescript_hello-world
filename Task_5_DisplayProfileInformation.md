# Display Profile Information

After we have successfully logged in we also want to update the `ProfileComponent` to have some Profile Information displayed.

### Update the ProfileComponent

- Open the `ProfileComponent`: `src/app/features/profile/profile.component.ts`
- You can see that all the Profile Informations are hard coded. Now we want to get the real data, so we can remove the whole mocked UserProfile.
- First we need to inject again the `AuthService` inside the `src/app/pages/profile/profile.component.ts`
- To receive User Information the `AuthService` provides an `user$`Observable we can subscribe to
- Now we want to display the User's profile picture, the username and the users email. We cat get this information from our `user$` Observable which hold the properties `email`, `picture` and `name`
- To see more what the `user` Object hold you can just display it's stringified version inside the template by using the `JSONPipe` for it.


```javascript
// src/app/features/profile/profile.component.ts

@Component({...})
export class ProfileComponent {
    title = "Decoded ID Token";

    user$ = this.auth.user$;

    code$ = this.user$.pipe(map((user) => JSON.stringify(user, null, 2)));

    constructor(private auth: AuthService) {}
}
```
