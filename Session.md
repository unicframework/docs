## Session

  A sessions provide way to store information about the user across multiple requests.


### Create a New Session

```php
//Create new session
$req->session->set('email', 'example@gmail.com');
```


### Get Session Data

```php
//Get session data
$req->session->email;
//OR
$req->session->get('email');
```


### Check Session Data

```php
//Get session exists or not
if($req->session->has('email')) {
  //Session data exists
} else {
  //Session data not exists
}
```


### Delete Session Data

```php
//Delete a session data
$req->session->delete('email');
```

  It will delete only session variable data.


### Delete Session

```php
//Delete all session
$req->session->destroy();
```

  It will delete all session data.
