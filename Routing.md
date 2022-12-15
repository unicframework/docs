## Routing

  In web application routing refers to determining how an application responds to a particular request.

  In unic framework each route can have one or more handler functions, which are executed when the route is matched.

Route definition in unic framework:

```php
$app->METHOD('PATH', HANDLER);
```
Where:
- `app` is an instance of unic app or http router.
- `METHOD` is an HTTP request method, in lowercase.
- `PATH` is a path or an endpoint on the server.
- `HANDLER` is the function executed when the route is matched.

## Examples

A simple get route, which return `Hello, World!` as homepage.
```php
$app->get('/', function($req, $res) {
  $res->send('Hello, World!');
});
```

A simple post route for `route(/)`:
```php
$app->post('/', function($req, $res) {
  $res->send('POST request on (/) homepage');
});
```

A simple put route for `route(/)`:
```php
$app->put('/', function($req, $res) {
  $res->send('PUT request on (/) homepage');
});
```

A simple delete route for `route(/)`:
```php
$app->delete('/', function($req, $res) {
  $res->send('DELETE request on (/) homepage');
});
```

A simple any get or post route for `route(/)`:
```php
$app->any(['get', 'post'], '/', function($req, $res) {
  $res->send("{$req->method} request on (/) homepage');
});
```

Respond to all http methods from `route(/)':
```php
$app->all('/', function($req, $res) {
  $res->send("{$req->method} request on (/) homepage');
});
```

Group routes:
```php
// Group routes
$app->group('/blog', function($router) {
  $router->get('/', function($req, $res) {
    $res->send("Ok");
  });

  $router->post('/', function($req, $res) {
    $res->send("Ok");
  });
});
```

Create routes using http router:

```php
use Unic\App;
use Unic\Router\HttpRouter;

$app = new App();
$router = new HttpRouter();

$router->get('/', function($req, $res) {
  $res->send("Ok");
});

$router->post('/{name}', function($req, $res) {
  $res->send($req->params->name);
});

$app->use('/blog', $router);
```
