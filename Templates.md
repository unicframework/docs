## Templates

  The Template is a presentation layer which handles user interface part of web application.

  Unic framework by default store all the template in templates directory, but you can change the template directory in settings.

#### Create a HTML template

  Create a `home.html` or `home.php` file in a templates directory and put the following code in it.

```html
<!DOCTYPE>
<html>
<head>
  <title>Hello, World</title>
</head>
<body>
  <h1>Hello, World!!</h1>
</body>
</html>
```
 This is a simple `Hello World` template file.

#### How to render templates

  Render your templates in views.

```php
class view extends Views {
  function home(Request $req) {
    //Render html templates
    return $this->render('home');
  }
}
```

#### How to pass data in templates

  We can pass any data in templates using array.

```php
class view extends Views {
  function home(Request $req) {
    //Data
    $blog = array(
      'title' => 'this is title',
      'author' => 'author name',
      'date' => '13-Fab-2020',
    );
    //Pass data to template
    return $this->render('home', $blog);
  }
}
```

#### How to access data in templates

```html
<!DOCTYPE>
<html>
<head>
  <title><?= $title; ?></title>
</head>
<body>
  <h1><?= $title; ?></h1>
  <h1><?= $author; ?></h1>
  <h1><?= $date; ?></h1>
</body>
</html>
```
