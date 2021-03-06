# Constants of `wp-config.php`

There are several PHP constants defined in the `wp-config.php` file that aid in debugging. Currently, there are three that you can switch on or off, they are:

- [`WP_DEBUG`](#wp-debug)
- [`WP_DEBUG_DISPLAY`](#wp-debug-display)
- [`WP_DEBUG_LOG`](#wp-debug-log)
- [`SCRIPT_DEBUG`](#script-debug)
- [`CONCATENATE_SCRIPTS`](#concat-scripts)
- [`SAVEQUERIES`](#save-queries)

---


### `WP_DEBUG`

Added in [WordPress version 2.3.1](http://codex.wordpress.org/Version_2.3.1), the WP_DEBUG option will display WordPress/PHP errors on the public facing web pages. This is handy for finding errors in your code that you may normally not see or know exist. By default this option is set to `false` which turns the errors off, but **all WordPress developers should have this option enabled during development**. However, you generally **never** want to leave this on in a production environment.

| Code | Action |
|---|---|
| `define( 'WP_DEBUG', true );` | Activates error reporting |
| `define( 'WP_DEBUG', false );` | Deactivates error reporting |

_*Note: Check that the values must be **bool** instead of **string**_

A minor patch later the on [Wordpress version 2.3.2](http://codex.wordpress.org/Version_2.3.2), the system allowed us to have a more granular control over the Database error logs.

Later on in the version 2.5, WordPress raised the [error reporting](http://www.php.net/error-reporting) level to E_ALL, that will allow to see logs for Notices and Deprecation messages.


###### _Notes:_

If you have this option turned on, you might encounter problems with AJAX requests, this problem is related to Notices been printed on the output of the AJAX response, that **will break XML and JSON**.


#### `WP_DEBUG_LOG`

When you use `WP_DEBUG` set to `true` you have access to this constant, and this will allow you to log your notices and warnings to a file.


#### `WP_DEBUG_DISPLAY`

When you use `WP_DEBUG` set to `true` you have access to this constant, with it you can choose to display or not the notices and warnings on the screen.


###### Note:

If these variables don't produce the output you are expecting check out the [Codex Section about ways to setup your logging](http://codex.wordpress.org/Editing_wp-config.php#Configure_Error_Logging).

---


### `SCRIPT_DEBUG`

When you have a WordPress plugin or theme that is including the Minified version of your CSS or JavaScript files by default you are doing it wrong!

Following the WordPress idea of creating a file for development and its minified version is very good and you should have both files in your plugin, and based on this variable you will enqueue one or the other.

By default this constant will be set to `false`, and if you want to be able to debug CSS or JavaScript files from WordPress you should turn it to `true`.


#### Activates the Logs

```php
define( 'SCRIPT_DEBUG', true );
```

_Check that the values must be **bool** instead of **string**_

WordPress default files `wp-includes` and `wp-admin` will be set to its development version if set to `true`.


### `CONCATENATE_SCRIPTS`

On your WordPress administration you will have all your JavaScript files concatenated in to one single request based on the dependencies and priority of enqueue.

To remove this feature all around you can set this constant to `false`.

```php
define( 'CONCATENATE_SCRIPTS', false );
```

---


### `SAVEQUERIES`

When you are dealing with the database you might want to save your queries so that you can debug what is happening inside of your plugin or theme.

**Make `$wpdb` save Queries**

```php
define( 'SAVEQUERIES', true );
```
_**Note:** this will slowdown your WordPress_
