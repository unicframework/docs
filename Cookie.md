## Cookie

  Cookie is a small piece of information which is stored at client browser. It is used to recognize the user.

  Cookie is created at server side and saved to client browser. Each time when client sends request to the server, cookie is embedded with request.

Create a new cookie:

```php
// Create new cookie
$req->cookies->set('email', 'example@gmail.com', time()+(60*30), '/');
```

Get the cookie data:

```php
// Get cookie data
$req->cookies->get('email');
```

Check cookie data exists or not:

```php
// Check cookie exists or not
if($req->cookies->has('email')) {
  // Cookie exists
} else {
  // Cookie not exists
}
```

Delete the cookie:

```php
// Delete cookie
$req->cookies->delete('email');
```
