# Unic Framework

<p align="center">
  <img src="unic-logo.jpg" width="400px" alt="Unic Logo">
</p>

Unic is a high performance, open source web application framework.
Unic web framework follows the MVT (Model-View-Template) architectural pattern.


## User Guide

- [Introduction](Introduction.md)
- [Installation](Installation.md)
- [Views](Views.md)
- [URLs](URLs.md)
- [Models](Models.md)
- [Templates](Templates.md)
- [Middlewares](Middlewares.md)
- [Static files](Static-files.md)
- [File Uploading](File-Uploading.md)
- [Session](Session.md)
- [Cookie](Cookie.md)
- [Request](Request.md)
- [Databases](Databases.md)
- [Security](Security.md)
- [ErrorHandler](ErrorHandler.md)
- [Settings](Settings.md)
- [How to Deploy](How-to-Deploy.md)


## Simple Example

  A simple `Hello, World` web application in unic framework.

### Create View

  Let’s write the first view. Open the `app/view.php` file and put the following PHP code in it:

```php
class view extends Views {
  //Home view
  function home(Request $req) {
    //Send response
    return $this->response('Hello, World !!');
  }
}
```

  `home` view is created, now map this view to URLs.

### Map URLs to Views

  Let's create URL and map to views. Open `app/urls.php` file and put the following code in it:

```php
//Include views
require_once 'view.php';

$urlpatterns = [
  '/' => 'view.home',
];
```

  Now a simple `Hello World` web app is created, it's so simple.


## Simple Web API Example

  A simple `Hello, World` web API in unic framework.

### Create View

  Let’s write the first view. Open the `app/view.php` file and put the following PHP code in it:

```php
class view extends Views {
  //Home view
  function home(Request $req) {
    $data = [
      'status' => true,
      'data' => 'Hello, World',
    ];
    //Send json response
    return $this->response_json($data);
  }
}
```

  `home` view is created, now map this view to URLs.

### Map URLs to Views

  Let's create URL and map to views. Open `app/urls.php` file and put the following code in it:

```php
//Include views
require_once 'view.php';

$urlpatterns = [
  '/' => 'view.home',
];
```

  Now a simple `Hello, World` web API is created.


## License

  [MIT License](https://github.com/unicframework/unic/blob/main/LICENSE)
