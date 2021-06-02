# Angular 12 JWT Authentication & Authorization example

## Flow for User Registration and User Login
For JWT – Token based Authentication with Web API, we’re gonna call 2 endpoints:
- POST `api/auth/signup` for User Registration
- POST `api/auth/signin` for User Login

You can take a look at following flow to have an overview of Requests and Responses that Angular 12 Client will make or receive.

![angular-12-jwt-authentication-flow](angular-12-jwt-authentication-flow.png)

## Angular JWT App Diagram with Router and HttpInterceptor
![angular-12-jwt-authentication-overview](angular-12-jwt-authentication-overview.png)

For more detail, please visit:
> [Angular 12 JWT Authentication & Authorization with Web API](https://bezkoder.com/angular-12-jwt-auth/)

## With Spring Boot back-end

> [Angular 12 + Spring Boot: JWT Authentication and Authorization example](https://bezkoder.com/angular-12-spring-boot-jwt-auth/)

## With Node.js Express back-end

> [Angular 12 + Node.js Express: JWT Authentication and Authorization example](https://bezkoder.com/node-js-angular-12-jwt-auth/)

Open `app/_helpers/auth.interceptor.js`, modify the code to work with **x-access-token** like this:
```js
...

// const TOKEN_HEADER_KEY = 'Authorization'; // for Spring Boot back-end
const TOKEN_HEADER_KEY = 'x-access-token';   // for Node.js Express back-end

@Injectable()
export class AuthInterceptor implements HttpInterceptor {
  ...

  intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
    ...
    if (token != null) {
      // for Spring Boot back-end
      // authReq = req.clone({ headers: req.headers.set(TOKEN_HEADER_KEY, 'Bearer ' + token) });

      // for Node.js Express back-end
      authReq = req.clone({ headers: req.headers.set(TOKEN_HEADER_KEY, token) });
    }
    return next.handle(authReq);
  }
}

...
```

Run `ng serve --port 8081` for a dev server. Navigate to `http://localhost:8081/`.

## More practice
> [Angular JWT Refresh Token example with Http Interceptor](https://www.bezkoder.com/angular-12-refresh-token/)

> [Angular CRUD Application example with Web API](https://bezkoder.com/angular-12-crud-app/)

> [Angular Pagination example | ngx-pagination](https://bezkoder.com/angular-12-pagination-ngx/)

> [Angular File upload example with progress bar & Bootstrap](https://bezkoder.com/angular-12-file-upload/)

Fullstack with Node.js Express:
> [Angular + Node.js Express + MySQL example](https://bezkoder.com/angular-12-node-js-express-mysql/)

> [Angular + Node.js Express + PostgreSQL example](https://bezkoder.com/angular-12-node-js-express-postgresql/)

> [Angular + Node.js Express + MongoDB example](https://bezkoder.com/angular-12-mongodb-node-js-express/)

> [Angular + Node.js Express: File upload example](https://bezkoder.com/angular-12-node-js-file-upload/)

Fullstack with Spring Boot:
> [Angular + Spring Boot + MySQL example](https://bezkoder.com/angular-12-spring-boot-mysql/)

> [Angular + Spring Boot + PostgreSQL example](https://bezkoder.com/angular-12-spring-boot-postgresql/)

> [Angular + Spring Boot + MongoDB example](https://bezkoder.com/angular-12-spring-boot-mongodb/)

> [Angular + Spring Boot: File upload example](https://bezkoder.com/angular-12-spring-boot-file-upload/)

Fullstack with Django:
> [Angular 12 + Django example](https://bezkoder.com/django-angular-12-crud-rest-framework/)

> [Angular + Django + MySQL](https://bezkoder.com/django-angular-mysql/)

> [Angular + Django + PostgreSQL](https://bezkoder.com/django-angular-postgresql/)

> [Angular + Django + MongoDB](https://bezkoder.com/django-angular-mongodb/)

Serverless with Firebase:
> [Angular 12 Firebase CRUD with Realtime DataBase | AngularFireDatabase](https://bezkoder.com/angular-12-firebase-crud/)

> [Angular 12 Firestore CRUD example with AngularFireStore](https://bezkoder.com/angular-12-firestore-crud-angularfirestore/)

> [Angular 12 Firebase Storage: File Upload/Display/Delete example](https://bezkoder.com/angular-12-file-upload-firebase-storage/)

Integration (run back-end & front-end on same server/port)
> [How to integrate Angular with Node.js Restful Services](https://bezkoder.com/integrate-angular-12-node-js/)

> [How to Integrate Angular with Spring Boot Rest API](https://bezkoder.com/integrate-angular-12-spring-boot/)