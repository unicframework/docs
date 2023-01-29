## Session

  A sessions provide way to store information about the user across multiple requests.

  Use session middleware to use session:
```php
$app->use($app->session());
```

Set session data:

```php
// Set new session data
$req->session->set('email', 'example@gmail.com');
```

Get the session data:

```php
// Get session data
$req->session->get('email');
```

Check session data exists or not:

```php
// Get session exists or not
if($req->session->has('email')) {
    // Session data exists
} else {
    // Session data not exists
}
```

Delete the session data:

```php
// Delete a session data
$req->session->delete('email');
```

It will delete only session variable data.


Delete the all session data:

```php
// Delete all session
$req->session->destroy();
```

It will delete all session data.
