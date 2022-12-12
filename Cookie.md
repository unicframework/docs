## Cookie

  Cookie is a small piece of information which is stored at client browser. It is used to recognize the user.

  Cookie is created at server side and saved to client browser. Each time when client sends request to the server, cookie is embedded with request.


### Create a New Cookie

```php
// Create new cookie
$req->cookies->set('email', 'example@gmail.com', time()+(60*30), '/');
```


### Get Cookie Data

```php
// Get cookie data
$req->cookies->get('email');
```

### Check Cookie Data

```php
// Check cookie exists or not
if($req->cookies->has('email')) {
  // Cookie exists
} else {
  // Cookie not exists
}
```


### Delete Cookie

```php
// Delete cookie
$req->cookies->delete('email');
```
