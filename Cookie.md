## Cookie

  Cookie is a small piece of information which is stored at client browser. It is used to recognize the user.

  Cookie is created at server side and saved to client browser. Each time when client sends request to the server, cookie is embedded with request.

Create a new cookie:

```php
$app->get('/', function($req, $res) {
    // Create new cookie
    $res->cookie('email', 'example@gmail.com', [
        'expire' => time()+(60*30),
        'path' => '/',
    ]);
});
```

Get the cookie data:

```php
$app->get('/', function($req, $res) {
    // Get cookie data
    $req->cookie('email');
});
```

Check cookie data exists or not:

```php
// Check cookie exists or not
if($req->cookie('email') !== null) {
    // Cookie exists
} else {
    // Cookie not exists
}
```

Delete the cookie:

```php
// Delete cookie
$req->removeCookie('email');
```
