## URLs

  Unic allows to create simple and clean urls routing without any limitation.

### Map URLs with Views

  Let's create URL and map to views. open `app/urls.php` file and put the following code in it:

```php
//Include views
require_once 'view.php';
require_once 'product.php';

$urlpatterns = [
  '/' => 'view.home',
  '/product/{id}' => 'product.data',
  '/about' => 'view.about',
];
```

### URL Patterns and slug

  Unic framework allows to create custom urls patterns.

  Example :
```
/product/1
/product/2
/product/3
```

  Here the product id is dynamic it can be change on every request.

```php
$urlpatterns = [
  '/product/{id}' => 'view.product',
];
```

  Here we can access product id with `$this->request->params` object.

```php
class view extends Views {
  function __construct() {
    parent::__construct();
  }

  function product() {
    //Get product id
    $id = $this->request->params->id;
    return $this->response('Product : '.$id);
  }
}
```

  Unic does not support any int, str, float type but you can use them in slug. `{slug}` support all the int, float, and string as well as wildcards.


### Include URLs

  Include your app URLs file in main URLs file.

```php
$urlpatterns = [
  //Blog app urls
  '/' => urls('blog/urls.php'),

  //Product app urls
  '/product' => urls('product/urls.php'),
];
```
