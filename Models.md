## Models

  Models are classes that are designed to work with database. It manages the database logic and rules of the web application.

### Create a model

  Let’s create the first model. Open the `app/model.php` file and put the following PHP code in it:

```php
class blog_model extends Models {
  private $title;
  private $author;
  private $date;

  function __construct() {
    //Create database connection
    $this->connect('db');
  }

  function get() {
    //Execute raw sql query
    $result = $this->db->query('select * from blog');
    return $result;
  }
}
```

### Use Model

  Include model files in views to use models in web application.

```php
//Include models
require_once 'model.php';

class view extends Views {
  private $blog;

  function __construct() {
    parent::__construct();

    //Create model object
    $this->blog = new blog_model();
  }

  function home() {
    //Get blog data from model
    $blog = $this->blog->get();
    //Response data
    return $this->response($blog);
  }
}
```
