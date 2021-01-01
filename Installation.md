## Installation

  Unic framework is for PHP, so it's requires PHP 5.6 or newer. Now you won’t need to setup anything just yet.

### Unic can be installed in few steps

  - [Download](https://github.com/unicframework/unic/archive/main.zip) the Unic files.
  - Unzip the package.
  - Upload all the Unic files and directories (application, system, .htaccess, index.php) on the server.

```
public_html
├── application
├── system
├── .htaccess
└── index.php
```

  That's it, in the Unic framework there is nothing to configure and setup. It's always ready to go.

### For Linux

  A quick setup for linux and android devices.

```sh
# Clone unic framework
git clone https://github.com/unicframework/unic

# Start web server
cd unic
php -S localhost:8080 index.php
```

  That's it, in the Unic web framework there is nothing to configure and setup. it's always ready to go.

### Install with composer

  - Install `composer` if you have not installed.

```shell
composer create-project unicframework/unic blog
```

  It will create a `blog` project for you.
