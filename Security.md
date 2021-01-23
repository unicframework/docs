## Security

  Security library provide basic security feature to the web application. unic framework provide CSRF, XSS and SQL Injection protection.

#### SQL Injection

  SQL Injection is a technique where an attacker creates or alters existing SQL commands to expose hidden data, or to override valuable ones, or even to execute dangerous system level commands on the database host. 

  **Avoid SQL Injection**

  - Use prepared statements.
  - Use database-specific string escape function (e.g. `mysql_real_escape_string()`, `sqlite_escape_string()`, etc.).

#### XSS

  Cross site scripting (XSS) is a common attack vector that injects malicious code into a vulnerable web application.
  Unic Framework provide XSS protection.

```php
class view extends Views {
  function blog(Request $req) {
    //XSS Clean
    $data = xss_clean($blog_data);
    return $this->response($data);
  }
}
```
  Use `xss_clean()` to avoid xss attack.


#### CSRF

  Cross site request forgery (CSRF), also known as XSRF, Sea Surf or Session Riding attack. CSRF is a type of malicious exploit of a website where unauthorized commands are transmitted from a user that the web application trusts.

  **Add CSRF Token :**

  Add CSRF Token in your web form to avoid CSRF attack.

```html
<form method="POST">
  <?= csrf_token(); ?>
  <input type="text" name="username" palceholder="Username">
  <input type="password" name="password" placeholder="Password">
  <input type="submit" name="submit" value="Login">
</form>
```

  **Add CSRF token in AJAX**

  Add CSRF token in Ajax request.

```javascript
$.ajax({
  type: "POST",
  url: "/login",
  data: {
    carf_token: "<?= get_csrf_token(); ?>",
    username: "user_name",
    password: "password"
  },
  success: function(data){
     //success response data
  }
});
```

  **Verify CSRF Token**

```php
class view extends Views {
  function login(Request $req) {
    //Form Submit
    if($req->is_post) {
      //Verify CSRF Token
      if(csrf_verify()) {
        //Valid CSRF Token
        $username = $req->post->username;
        $password = $req->post->password;
      } else {
        //Invalid CSRF Token
      }
    } else {
      //Render Login Page
      return $this->render('login');
    }
  }
}
```

  Add CSRF token in your web form and verify that token, to authenticate the web form and avoid CSRF attack.
