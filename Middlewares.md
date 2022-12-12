## Middleware

  A Middleware is a small piece of code that is used to alter web application `request/response` cycle.
  Middlewares are building block of unic framework, in unic everything is middleware.

### Create Middleware

  Let's create a middleware.

```php
use Unic\App;

$app = new App();

$app->use(function($req, $res, $next) {
  $req->counter = 0;
  // Calls next middleware
  $next();
});

$app->use(function($req, $res, $next) {
  $req->counter++;
  $next();
});
```

  Make sure to call next function in middleware to run next middleware otherwise it will never calls the next middleware.
