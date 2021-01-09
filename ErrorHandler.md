## ErrorHandler

  Error Handler's used to handle errors like 404 (page not found), 500 (Internal Server Error), etc.

  Create your custom ErrorHandler to handle any server error.

### Create custom errorhandler

  1. Create your ErrorHandler view.

```php
class view extends Views {
  function __construct() {
    parent::__construct();
  }

  //Page not found error handler
  function page_not_found() {
    return $this->response('404 Page Not Found', 404);
  }

  //Account blocked error handler
  function blocked_error() {
    return $this->response('Your account has been blocked!', 500);
  }
}
```

  2. Include your views to urls file.
  3. Map your handler with errorhandler array.

```php
$errorhandlers = [
  '404' => 'view.page_not_found',
  'blocked' => 'view.blocked_error',
];
```

  It will redirect all `404` and `blocked` errors to your `page_not_found` and `blocled_error` views.

  ***Note : The ErrorHandler array, it must be inside the main urls file only.***

### Raise custom errors

  Unic framework allows us to raise custom errors.

```php
class view extends Views {
  function __construct() {
    parent::__construct();
  }

  function home() {
    //Raise 404 page not found error
    $this->raise('404');

    //Raise 500 page not found error
    $this->raise('500');

    //Raise custom error
    $this->raise('blocked');
  }
}
```
