## Views

Unic framework support multiple view engine like php, twig etc.

Let's set the view directory path:
```php
$app->set('views', base_path('views'));
```

Let's set the view engine:
```php
$app->set('view_engine', 'twig');
```

Let's render a view:
```php
$app->get('/', function($req, $res) {
    $res->render('index.twig');
});
```

Pass data to the views:
```php
$app->get('/', function($req, $res) {
    $res->locals->a = 10;
    $res->render('index.twig', [
        'title' => 'Unic',
    ]);
});
```

The `$res->locals` variables are by default accessible from views.
