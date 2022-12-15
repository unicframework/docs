## Session

  A sessions provide way to store information about the user across multiple requests.

Create a new session:

```php
// Create new session
$req->sessions->set('email', 'example@gmail.com');
```

Get the session data:

```php
// Get session data
$req->sessions->get('email');
```

Check session data exists or not:

```php
// Get session exists or not
if($req->sessions->has('email')) {
  // Session data exists
} else {
  // Session data not exists
}
```

Delete the session data:

```php
// Delete a session data
$req->sessions->delete('email');
```

It will delete only session variable data.


Delete the all session data:

```php
// Delete all session
$req->sessions->destroy();
```

It will delete all session data.
