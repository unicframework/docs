## Static files

  Websites need some static files like images, js and css etc, to server these static files use the `static('URL', 'DIR_PATH')` method to set the static directory path and url.

```php
use Unic\App;

$app = new App();
$app->static('/public', base_path('/public'));
```

Generate static files url in templates.

```html
<!DOCTYPE>
<html>
<head>
    <title>cat image</title>
</head>
<body>
    <img src="<?= asset('/img/cat.jpg'); ?>" alt="cat image"/>
</body>
</html>
```

The `asset()` function generate full URL for static files.
