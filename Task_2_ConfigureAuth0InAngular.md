# Configuring the SDK in the app

### Add the Auth0 configuration variables to Angular
From the Auth0 Application Settings page, you need the Auth0 Domain and Client ID values to allow your Angular application to use the communication bridge you just created.

// ToDo manage .env file

### Import AuthModule into you AppModule

- Import the `environment.ts` inside `src/app/app.module.ts`
- Add `AuthModule` into the `imports` Array of th `NgModule`-Decorator.
- Use the `forRoot` call to give in the `auth` Properties in our `environment` file


### Hints

```javascript
// src/environments/environment.ts

import { domain, clientId } from '../../auth_config.json';

export const environment = {
  production: false,
  auth: {
    domain,
    clientId,
    redirectUri: window.location.origin,
  },
};

// src/app/app.module.ts
import { AuthModule } from '@auth0/auth0-angular';
import { environment as env } from '../environments/environment';

...

@NgModule({
    declarations: [...],
    imports: [
        BrowserModule,
        AppRoutingModule,
        HttpClientModule,
        SharedModule,
        // 👇 add and initialize AuthModule
        AuthModule.forRoot({
            ...env.auth,
        }),
```
