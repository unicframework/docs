## Views

Unic framework support multiple view engine like php, twig etc.

Let's set the default view directory path:
```php
$app->set('views', base_path('views'));
```

Let's set the view engine:
```php
$app->set('view_engine', 'twig');
```

Now let's create a view inside the views directory:
```html
<!DOCTYPE html>
<html>
    <head>
        <title>{{ title }}</title>
    </head>
    <body>
        {{ title }}
    </body>
</html>
```

Let's render a view:
```php
$app->get('/', function($req, $res) {
    $res->render('index.twig');
});
```

We can pass data to the views:
```php
$app->get('/', function($req, $res) {
    $res->locals->a = 10;
    $res->render('index.twig', [
        'title' => 'Unic',
    ]);
});
```

The `$res->locals` variables are by default accessible from views.
