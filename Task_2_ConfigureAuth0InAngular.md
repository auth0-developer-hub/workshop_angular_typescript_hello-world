# Configuring the SDK in the app

### Add the Auth0 configuration variables to Angular
From the Auth0 Application Settings page, you need the Auth0 Domain and Client ID values to allow your Angular application to use the communication bridge you just created.

Create a .env file under the root project directory and populate it with the following environment variables:

```
// .env
AUTH0_DOMAIN=AUTH0-DOMAIN
AUTH0_CLIENT_ID=AUTH0-CLIENT-ID
AUTH0_CALLBACK_URL=http://localhost:4040/callback
API_SERVER_URL=http://localhost:6060
```

### Import AuthModule into you AppModule

- Import the `environment.ts` inside `src/app/app.module.ts`
- Add `AuthModule` into the `imports` Array of th `NgModule`-Decorator.
- Use the `forRoot` call to give in the `auth` Properties in our `environment` file

### Add the Auth0 configuration variables to Angular

### Hints

```javascript

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
            ...env.auth0,
        }),
```
