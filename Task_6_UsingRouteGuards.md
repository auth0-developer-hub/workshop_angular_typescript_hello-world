# Protect the profile and external API routes with a guard.

Some pages inside our Angular application should be protected unless the user is authenticated.
For that the `Auth0-SDK` provides a build in Routing-Guard to add ass an `CanActivate` Guard.

- Update the `AppRoutingModule` by adding the `AuthGuard` to following routes:
  - 'profile'
  - 'external-api'

**After you added the `AuthGuard` you should not be able to visit the `profile` Route without signing in.**

```JavaScript
// src/app/app-routing.module.ts

import { AuthGuard } from '@auth0/auth0-angular';

const APP_ROUTES: Routes = [
    ...
  {
    path: 'profile',
    component: ProfileComponent,
    canActivate: [AuthGuard],
  },
  {
    path: 'external-api',
    component: ExternalApiComponent,
    canActivate: [AuthGuard],
  },
];

```
