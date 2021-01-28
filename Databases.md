## Databases

  Unic framework support pdo, mysqli, sqlite database driver's.

#### Database Configuration

  Configure your databse settings in settings file.

```php
$db['db']= [
    'dsn' => '',
    'hostname' => 'localhost',
    'port' => '',
    'username' => 'demo_user',
    'password' => '1234',
    'database' => 'demo',
    'driver' => 'mysqli',
    'char_set' => 'utf8',
];
```

  - **dsn** : The full DSN string describe a connection to the database. by default you can leav it will blank.
  - **hostname** : The hostname of your database server.
  - **port** : The port of your database server.
  - **username** : The username used to connect to the database.
  - **password** : The password used to connect to the database.
  - **database** : The name of the database you want to connect to.
  - **driver** : The name of the database driver (mysqli, pdo, sqlite3).
  - **char_set** : The character set used in communicating with the database.


#### Database Connection

  Configure your database settings and initialize database connection.

```php
class model extends Models {
  function blog() {
    //Initialize database
    $this->connect('db');
    $this->connect('blog_db');

    //OR
    $this->connect('db', 'blog_db');

    //Close database connection
    $this->db->close();
    $this->blog_db->close();
  }
}
```


#### Database Query

  Unic framework support simple database query.

```php
class blog_model extends Models {
  function __construct() {
    //Initialize database connection
    $this->connect('blog_db');
  }

  function get_data() {
    //Get data from db
    $result = $this->blog_db->query('select * from blog');
    return $result;
  }
}
```
