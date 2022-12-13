## Routing

  Unic framework provide very simple routing.

  Let's create routes in unic framework.

```php
use Unic\App;

$app->get('/', function($req, $res) {
  $res->send("Ok");
});

$app->post('/', function($req, $res) {
  $res->send("Ok");
});

$app->put('/', function($req, $res) {
  $res->send("Ok");
});

$app->delete('/', function($req, $res) {
  $res->send("Ok");
});

$app->any(['get', 'post'], '/', function($req, $res) {
  $res->send('Ok');
});

$app->all('/blog/{name}', function($req, $res) {
  $res->send($req->params->name);
});

// Group routes
$app->use('/blog', function($router) {
  $router->get('/', function($req, $res) {
    $res->send("Ok");
  });

  $router->post('/', function($req, $res) {
    $res->send("Ok");
  });
});
```

We can use http router to create routes.

```php
use Unic\App;
use Unic\Router\HttpRouter;

$app = new App();
$router = new HttpRouter();

$router->get('/', function($req, $res) {
  $res->send("Ok");
});

$router->post('/', function($req, $res) {
  $res->send("Ok");
});

$app->use($router);
```
