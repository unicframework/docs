## Static files

  Websites need some static files like images, js and css etc, to server these static files use the `static('URL', 'DIR_PATH')` method to set the static directory path and url.

```php
use Unic\App;

$app = new App();

// Set public path
$app->use($app->static('/public', __DIR__ . '/public'));
```

Generate static files url in templates.

```php
$app->get('/', function($req, $res) {
    // Generate url of static files based on public path
    $req->app->asset('/path/to/cat.png');
});
```

The `$req->app->asset()` function generate full URL for static files.
