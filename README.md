# Identity 101 workshop

## Workshop Overview
This workshop will follow 7 steps:

**Task 1:** Install the Auth0 SDK and create the application in Auth0.  
**Task 2:** Configure the SDK in the app.    
**Task 3:** Add a log in button.  
**Task 4:** Add a log out button.  
**Task 5:** Display profile information.  
**Task 6:** Protect the profile page with a guard.
**Task 7:** Call a protected endpoint using an `HttpInterceptor`.

Each step has a corresponding branch with the finished code for that step. If you get behind, you can always skip ahead by checking out the next branch.

Feel free to [follow along with the slides](https://drive.google.com/drive/folders/1y8EF3r3GGrj3eugR0xQLC53BcySbM5XD?usp=sharing) as well.

## About this App
This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 15.0.0. It also includes a tiny Express server for testing a public and a protected endpoint.

You'll find the demo project on [GitHub](https://github.com/auth0-developer-hub/spa_angular_typescript_hello-world___workshop):

Clone the Repo as following:

`git clone -b starter https://github.com/auth0-developer-hub/spa_angular_typescript_hello-world___workshop.git `

## Sign up for Auth0
If you haven't already, [sign up for a free Auth0 account](https://auth0.com/signup), which offers you:

* 7,000 [free active users and unlimited logins](https://auth0.com/pricing/).
* A [centralized, ready-to-ship login page](https://auth0.com/universal-login) for Web, iOS & Android.
* Up to 2 [social identity providers](https://auth0.com/docs/connections/identity-providers-social) like Google and Facebook login.
* Unlimited [serverless Rules](https://auth0.com/docs/rules/current) to customize and extend Auth0's capabilities.

During the sign-up process, you create something called an [Auth0 Tenant](https://auth0.com/docs/getting-started/the-basics#account-and-tenants), which is a container that Auth0 uses to store your identity service configuration and your users in isolation. No other Auth0 customer can peek into or access your tenant.
