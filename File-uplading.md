## File Uploading

File uploading is very simple and easy in unic framework.

Get uploaded file data:
```php
$app->post('/file', function($req, $res) {
    // Get all file details
    $res->json($req->files());
});
```
