## File Uploading

File uploading is very simple and easy in unic framework.

Let's handle file uploading:
```php
$app->post('/file', function($req, $res) {
    // Save uploaded file
    if ($req->files->has('image')) {
        $req->files->get('image')->save(base_path('public'));
    }
    // Get all file details
    $res->json($req->files->getAll());
});
```

We can access uploaded file details using `$req->files` object.

Change uploaded file name:

```php
$req->files->get('image')->save(base_path('public'), 'cat.png');
```
