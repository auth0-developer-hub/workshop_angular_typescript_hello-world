# Install the Auth0 SDK and create the application in Auth0.  

##  Create the Client Application in Auth0
Once you sign in, Auth0 takes you to the [Dashboard](https://manage.auth0.com/), where you can manage and configure your identity services. In the left sidebar menu, click on ["Applications"](https://manage.auth0.com/#/applications).

Then, click the "Create Application" button. A modal opens up with a form to provide a name for the application and choose its type.

**Name:** Auth0 Angular Workshop  
**Application Type:** Single Page Web Applications

Click the "Create" button to complete the process. Your Auth0 application page loads up.

We need now need to help Angular and Auth0 communicate using configuration data from that page.

Click on the "Settings" tab of your Auth0 Application page and fill in the following values:

**Allowed Callback URL:** http://localhost:4200

After your users successfully log in, Auth0 can only redirect them to any of the URLs you list here.

**Allowed Logout URL:** http://localhost:4200

After your users log out, Auth0 can only redirect them to any of the URLs you list here.

**Allowed Web Origins:** http://localhost:4200

Using the Auth0 Angular SDK, your Angular application will make requests under the hood to an Auth0 URL to handle authentication requests. As such, you need to add your Angular application origin URL to avoid Cross-Origin Resource Sharing (CORS) issues.

Scroll down and click the "Save Changes" button.

Don't close this page yet as you'll need some of its information in the next section.

### Add the Auth0 configuration variables to Angular
From the Auth0 Application Settings page, you need the Auth0 Domain and Client ID values to allow your Angular application to use the communication bridge you just created.

The client uses the `auth_config.json` file. Duplicate `auth_config.json.example` and remove the `.example`. Replace the `domain` and `clientId` values for now. You'll replace the `audience` value in step 7 when we set up the API.
