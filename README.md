## Unic Framework

<p align="center">
  <img src="unic-logo.jpg" width="400px" alt="Unic Logo">
</p>

Unic is a high performance, open source web application framework.
Unic framework is fast, minimal and unopinionated web framework inspired by express.
Unic is simple and flexible and provide lots of features to create apis and web application quickly.

## Features
  - Fast and flexible.
  - Extremely light weight.
  - Minimal and unopinionated.
  - Simple and robust routing.
  - Robust middlewares.

## User Guide

- [Installation](Installation.md)
- [Routing](Routing.md)
- [Middlewares](Middlewares.md)
- [Response](Response.md)
- [Views](Views.md)
- [Static files](Static-files.md)
- [Session](Session.md)
- [Cookie](Cookie.md)
- [File Uploading](File-uplading.md)

## Simple Example

  A simple `Hello, World` web application in unic framework.

```php
use Unic\App;

$app = new App();

$app->get('/', function($req, $res) {
    $res->send('Hello, World!');
});

$app->get('/api', function($req, $res) {
    $res->json([
        'status' => 'Ok',
    ]);
});

$app->start();
```

## OpenSwoole Example

  A simple `Hello, World` web application in unic framework using [OpenSwoole](https://openswoole.com) server.

```php
use Unic\App;
use OpenSwoole\Http\Server;

$app = new App();
$server = new Server("127.0.0.1", 3000);

$app->get('/', function($req, $res) {
    $res->send('Hello, World!');
});

$app->get('/api', function($req, $res) {
    $res->json([
        'status' => 'Ok',
    ]);
});

$app->useOpenSwooleServer($server);
$app->start();
```

Run OpenSwoole app:
```shell
php server.php
```

It start openswoole server at [localhost](http://localhost:3000)
## License

  [MIT License](https://github.com/unicframework/unic/blob/main/LICENSE)
