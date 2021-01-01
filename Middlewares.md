## Middleware

  A Middleware is a small piece of code that is used to alter web application `request/response` cycle.

### Create Middleware

  Let's create a `middleware.php` file inside your `app` directory, you can name it anything. Your middleware class name and filename must be the same.

```php
class middleware extends Middlewares {
  function __construct() {
    parent::__construct();
  }

  function hello() {
    $this->request->hello = 'Hello, World!';
  }
}
```

  This is a example of `Hello, World` middleware. This middleware will add a `hello` variable in request object.

### Global Middleware

  A global middleware execute on every request. Go to application `settings.php` file and add middleware in middlewares array.

```php
//Install your middlewares
$middlewares = [
  'app/middleware.hello',
];
```

### Local Middleware

  A local middlewares runs only when a specific view (Routes) is called. We can set local middleware in `urls.php` file.

```php
$urlpatterns = [
  '/' => 'view.home',
  //Local middleware
  '/hello' => [
    'view' => 'view.hello',
    'middleware' => 'app/middleware.hello'
  ],
];
```


### Group Middleware

  We can set group middleware in `urls.php` file.

```php
$urlpatterns = [
  '/' => 'view.home',
  //Group middlewares
  [
    'view' => [
      '/blog',
      '/blog/new',
      '/blog/delete'
    ],
    'middleware' => [
      'app/middleware.hello'
    ]
  ],
];
```
