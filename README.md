## Unic Framework

<p align="center">
  <img src="unic-logo.jpg" width="400px" alt="Unic Logo">
</p>

Unic is a high performance, open source web application framework.
Unic framework is fast, minimal and unopinionated web framework inspired by express.

## Features
  - Fast and Powerful.
  - Extremely Light Weight.
  - Minimal and unopinionated.
  - Simple routing.
  - Middlewares.

## User Guide

- [Installation](Installation.md)
- [Routing](Routing.md)
- [Middlewares](Middlewares.md)
- [Static files](Static-files.md)
- [Session](Session.md)
- [Cookie](Cookie.md)

## Simple Example

  A simple `Hello, World` web application in unic framework.

```php
use Unic\App;

$app = new App();

$app->get('/', function($req, $res) {
  $res->send("Hello, World!");
});

$app->start();
```

## License

  [MIT License](https://github.com/unicframework/unic/blob/main/LICENSE)
