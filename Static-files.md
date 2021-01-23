## Static files

  Websites are need some static files, these static files are js, css, images etc. Unic framework help us to manage these static files.

  - Set your static files directory in settings file.

```php
//Static files directory
$static_dir = '/static';
```

  - Set your static URL in settings file.

```php
//Static files URL
$static_url = '/';
```

  - Use static files in templates.

```html
<!DOCTYPE>
<html>
<head>
  <title>cat image</title>
</head>
<body>
  <img src='<?= static_url('/img/cat.jpg'); ?>' alt='cat image'/>
</body>
</html>
```

  - `static_url()` function return full URL of given file.
