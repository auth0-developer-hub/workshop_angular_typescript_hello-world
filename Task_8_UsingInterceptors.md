# Call a protected endpoint using an HttpInterceptor

Not everyone should have access to our data. That said most backends protecting their API and we need an AccessToken that prooves 
we have the right privileges to access the data.
This is done by setting the `Authentication` Header inside our Http Requests. We could do this manually on each
request, or we use an Angular Interceptor.
These Interceptors intercepts an Http call before it gets send out to the API. Hence we can easily apply the `Authorization` inside
our Interceptor

The Auth0-SDK already provides us some kind of `AuthHttpInterceptor` doing this already out of the box.

### Import the HTTP_INTERCEPTORS token and the AuthHttpInterceptor

- Provide the `HTTP_INTERCEPTORS` token inside the `AppModule` and use the `AuthHttpInterceptor` imported from `@auth0/auth0-angular`
- Update the configuration of the `AuthModule`:

```javascript
@NgModule({
  ...
  imports: [
    // 👇 update AuthModule
    AuthModule.forRoot({
      ...env.auth,
      httpInterceptor: {
        allowedList: [`${env.dev.apiUrl}/api/messages/protected-message`],
      },
    }),
  ],

```

### Update ExternalApiComponent

Having the interceptor applied we now want to test it with an protected API
Let's add another `callSecureApi` Function inside the `ExternalApiComponent`:

```javascript
export class ExternalApiComponent implements OnInit {
  message: string = null;

  constructor(private http: HttpClient) {}

  ngOnInit(): void {}

 callSecureApi(): void {
    this.http
      .get(`${env.dev.apiUrl}/api/messages/protected-message`)
      .subscribe((result: Message) => {
        this.message = result.message;
      });
  }
```

```html
<button (click)="callSecureApi()" type="button" class="btn btn-primary">
      Get Private Message
</button>
```

**After you have applied everything you should see a protected message returned from your running express backend**
