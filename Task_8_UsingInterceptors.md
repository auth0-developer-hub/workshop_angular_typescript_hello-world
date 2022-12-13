# Set up an API in Auth0 and configure the server and Angular app.

This process is similar to how you connected Angular with Auth0.

Head to [the APIs section in the Auth0 Dashboard](https://manage.auth0.com/#/apis), and hit the "Create API" button.

Then, in the form that Auth0 shows you can add a name and create an identifier. You can pick whatever you'd like or you can use these values:

**Name:** Angular Workshop API  
**Identifier:** https://angular-workshop-api

Leave the signing algorithm as RS256 as it's the best option from a security standpoint.

Identifiers are unique strings that help Auth0 differentiate between your different APIs. We recommend using URLs to create unique identifiers predictably; however, Auth0 never calls these URLs.

With these values in place, hit the "Create" button.

### Add the Auth0 configuration variables to Express
Now, click on the "Quick Start" tab of your Auth0 API page. This page presents instructions on how to set up different APIs. From the code box, choose "Node.js". Keep this page open as you'll be using the values next.

The server config uses a `.env` file at the root of the project.

Head back to the "Node.js" code snippet from the Auth0 API "Quick Start" page. Locate the definition of `jwtCheck`:

```js
var jwtCheck = jwt({
  secret: jwks.expressJwtSecret({
    cache: true,
    rateLimit: true,
    jwksRequestsPerMinute: 5,
    jwksUri: "https://<TENANT-NAME>.auth0.com/.well-known/jwks.json",
  }),
  audience: "https://angular-workshop-api", // 👈 AUTH0_AUDIENCE value
  issuer: "https://<TENANT-NAME>.auth0.com/", // 👈 AUTH0_ISSUER_URL value
  algorithms: ["RS256"],
});
```

Look at the object that the jwt function takes as an argument and use the following properties to complete the values of your `.env` file:

The value of `AUTH0_AUDIENCE` is the value of its `audience` property.

The value of `AUTH0_ISSUER` is the value of its `issuer` property.

Do not include the quotes, only the string value.

### Configure Angular to connect with the Express API
Head back to the `src` project directory that stores the Angular application.

Locate the `auth_config.json` file and replace the `audience` property with the same one you just added to the `.env` file for the Express server.

In the next steps of the workshop, you'll use those values in the `environment.ts` file and work on calling public and private endpoints.
