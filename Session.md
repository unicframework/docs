## Session

  A sessions provide way to store information about the user across multiple requests.

### Create a New Session

```php
// Create new session
$req->sessions->set('email', 'example@gmail.com');
```


### Get Session Data

```php
// Get session data
$req->sessions->get('email');
```


### Check Session Data

```php
// Get session exists or not
if($req->sessions->has('email')) {
  // Session data exists
} else {
  // Session data not exists
}
```


### Delete Session Data

```php
// Delete a session data
$req->sessions->delete('email');
```

  It will delete only session variable data.


### Delete Session

```php
// Delete all session
$req->sessions->destroy();
```

  It will delete all session data.
