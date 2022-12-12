## Static files

  Websites need some static files, these static files are js, css, images etc. Unic framework help us to manage these static files.

  - Set your static files directory in unic.

```php
use Unic\App;

$app = new App();
$app->static('/public', base_path('/public'));
```

  - Use static files urls in templates.

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

  - `asset()` function return full URL of given file.
