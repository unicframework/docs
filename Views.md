## Views

  Views are classes that render templates, communicate with models and contain all the business logic of web application.

  Generally all the views are written in a `views.php` file that is inside your application directory or apps directory, but you can create your own views file in unic framework.

### Create a view

  Let’s write the first view. Open the `app/view.php` file and put the following PHP code in it:

```php
class view extends Views {
  function __construct() {
    parent::__construct();
  }
  //Home view
  function home() {
    //Send response
    return $this->response('Hello, World !!');
  }
}
```

  A simple `Hello World` view is created, to render views map your view to URLs.


### Render Html templates

  Render html templates, crate a template `hello.html` or `hello.php` in templates directory.

```php
class view extends Views {
  function __construct() {
    parent::__construct();
  }

  function home() {
    //Render HTML templats
    return $this->render('home');
  }
}
```

### Render Files

  Render files like (CSS, JS, Images, etc.) to browser.

```php
class view extends Views {
  function __construct() {
    parent::__construct();
  }

  function home() {
    //Render files to browser.
    return $this->render_file('cat.jpg');
  }
}
```


### Send Files

  Send downloadable file like (css, js, images, audio, video etc.) to the client browser.

```php
class view extends Views {
  function __construct() {
    parent::__construct();
  }

  function home() {
    //Send downloadable files to client browser.
    return $this->send_file('cat.jpg');
  }
}
```


### Send String Response

  **Response a simple string :**

```php
class view extends Views {
  function __construct() {
    parent::__construct();
  }

  function home() {
    //Response string data
    return $this->response('Hello, World!');
  }
}
```

  **Response simple string with http response code :**

```php
class view extends Views {
  function __construct() {
    parent::__construct();
  }

  function home() {
    //Response string with http response code
    return $this->response('404 Page not found !!', 404);
  }
}
```

### Send Json Response

```php
class view extends Views {
  function __construct() {
    parent::__construct();
  }

  function home() {
    //Response json data
    return $this->response_json(['data' => 'hello world']);
  }
}
```

### Set Http Response code

```php
class view extends Views {
  function __construct() {
    parent::__construct();
  }

  function home() {
    //Set http response code
    $this->response_code(404);
    //Send response
    return $this->response('Page Not Found');
  }
}
```

### Set Http Response header

  Set Http Response header :

```php
class view extends Views {
  function __construct() {
    parent::__construct();
  }

  function home() {
    //Set response header
    $this->header('Content-Type: application/json');

    //Response data
    return $this->response('<h1>hello world</h1>');
  }
}
```

### Use Models

  Create a model `blog` and include models file in views.

```php
//Include models
require_once 'blog_model.php';

class view extends Views {
  private $blog;

  function __construct() {
    parent::__construct();

    //Create model object
    $this->blog = new blog_model();
  }

  function home() {
    //Get blogs data
    $blog = $this->blog->get();
    //Response blog data
    return $this->response($blog);
  }
}
```
