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
    // Call next middleware
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
    // Calls next middleware
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
    $res->send('Internal Server Error', 500);
});
```

  Unic framework automatically catche error and call error-handling middlewares, but you can manually call error-handling middleware. If we pass error as an argument in `$next()` function, it will skip all middlewares and only calls error-handling middlewares.

```php
$app->get('/', function($req, $res) {
    $next('error');
});

$app->use(function($err, $req, $res, $next) {
    $res->send('Internal Server Error', 500);
});
```
