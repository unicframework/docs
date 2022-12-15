## Middleware

  A Middleware is a small piece of code that is used to alter web application `request/response` cycle, middleware function has access of request, response object and next middleware function in reques/response cycle. 
  Middlewares are the building block of unic framework.

Middleware functions can be used to perform following tasks:
- Execute any code.
- Make changes to the request/response objects.
- End the request/response cycle.
- Call the next middleware function in the stack.

If the current middleware function does not end the request/response cycle, it must call next() to pass control to the next middleware function.

Types of middlewares in unic framework:
- Global middleware
- Route middleware
- Error-handling middleware

### Global Middleware

  Let's create a global middleware.

```php
$app->use(function($req, $res, $next) {
  $req->counter = 0;
  // Calls the next middleware
  $next();
});

$app->use(function($req, $res, $next) {
  $req->counter++;
  $next();
});
```

### Route Middleware

  Let's create a route middleware.

```php
$app->get('/', function($req, $res, $next) {
  $req->counter = 0;
  // Calls the next middleware
  $next();
}, function($req, $res) {
  $res->send("Counter is {$req->counter}");
});
```

### Error-handling Middleware

  Error-handling middleware always takes four arguments.
  You must provide four arguments to identify it as an error-handling middleware function.

  Let's create a error-handling middleware.

```php
$app->use(function($err, $req, $res, $next) {
  $res->status(500)->send('Internal Server Error');
});
```

