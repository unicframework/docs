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

## Route Methods

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
    $res->send("{$req->method} request on (/) homepage");
});
```

Respond to all http methods from `route(/)`:
```php
$app->all('/', function($req, $res) {
    $res->send("{$req->method} request on (/) homepage");
});
```

Unic framework support wide range of http methods like get, post, put, delete, patch, options, head, lock, merge, purge, trace, unlock etc.

## Route parameters

Route parameters are named URL segments that are used to capture the values specified at their position in the URL. 
```php
$app->get('/hello/{name}', function($req, $res) {
    $res->send("Hello, {$req->params->name}");
});
```
## Named Routes

Named routes are used to generate the URLs for route by using unique name. We can specify a name for a route by chaining the name method on the route definition.
```php
$app->get('/dashboard', function($req, $res) {
    $res->send("Hello, {$req->params->name}");
})->name('home');
```
Route name should be unique for each route.

Generate route url using named route.
```php
$app->get('/', function($req, $res) {
  $res->redirect($req->app->route('home'));
});
```
It will redirect to `/dashboard` route.

## Group Routes

Group all routes in single prefix.

```php
// Group routes
$app->group('/blog', function($router) {
    $router->get('/', function($req, $res) {
        $res->send('/blog');
    });

    $router->post('/create', function($req, $res) {
        $res->send('/blog/create');
    });
});
```

## Http Router

Create routes using HttpRouter:

```php
use Unic\App;
use Unic\Router\HttpRouter;

$app = new App();
$router = new HttpRouter();

$router->get('/', function($req, $res) {
    $res->send('Ok');
});

$router->post('/create', function($req, $res) {
    $res->send('Ok');
});

$app->use('/blog', $router);
```
