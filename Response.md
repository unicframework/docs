## Response

An HTTP response consists of a header and optional body, header contains metadata about body and body contains data.

## String Response

Let's send a text format response.

```php
$app->get('/', function($req, $res) {
  $res->send('Hello, World!');
});
```

## Json Response

Let's send a json response.

```php
$app->get('/', function($req, $res) {
  $res->json([
    'status' => 'Ok',
  ]);
});
```

## Set Http Status Code

Let's set http status code to the response.

```php
$app->get('/', function($req, $res) {
  $res->send('Hello, World!', 200);
});

$app->get('/', function($req, $res) {
  $res->status(200)->send('Hello, World!');
});

$app->get('/', function($req, $res) {
  // Send only http status code
  $res->sendStatus(200);
});
```

## Set Header

Let's set http header to the response.

```php
$app->get('/', function($req, $res) {
  $res->header('Content-Type', 'text/html')->send('Hello, World!');
});

$app->get('/', function($req, $res) {
  $res->header([
    'Content-Type' => 'text/html'
  ])->send('Hello, World!');
});

$app->get('/', function($req, $res) {
  $res->header('Content-Type', 'text/html');
  $res->send('Hello, World!');
});
```

## Remove Header

Let's remove http header from the response.

```php
$app->get('/', function($req, $res) {
  $res->removeHeader('Content-Type', 'text/html')->send('Hello, World!');
});

$app->get('/', function($req, $res) {
  $res->removeHeader([
    'Content-Type' => 'text/html'
  ])->send('Hello, World!');
});

$app->get('/', function($req, $res) {
  $res->removeHeader('Content-Type', 'text/html');
  $res->send('Hello, World!');
});
```

## File Response

Let's send file as a response.

```php
$app->get('/', function($req, $res) {
  $res->file('/cat-image.png');
});

$app->get('/', function($req, $res) {
  // Set file mime type
  $res->file('/cat-image.png', 'image/png');
});
```

## Download File

Let's download file from response.

```php
$app->get('/', function($req, $res) {
  $res->sendFile('/cat-image.png');
});

$app->get('/', function($req, $res) {
  // Set custom file name
  $res->sendFile('/cat-image.png', 'not-cat-image.png');
});
```

## Redirect

Let's redirect to another url.

```php
$app->get('/', function($req, $res) {
  $res->redirect('http://example.com');
});

$app->get('/', function($req, $res) {
  $res->redirect('http://example.com', 305);
});
```
