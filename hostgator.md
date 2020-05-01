# VPS

## Email

### Habilitando HTML inline em HORDE

Edite o arquivo `/usr/local/cpanel/base/horde/imp/config/mime_drivers.php`

```php
/* HTML driver settings */
    'html' => array(
        /* NOTE: Inline HTML display is turned OFF by default. */
        // 'inline' => false // default
        'inline' => true,
        'handles' => array(
            'text/html'
        ),
	    'icons' => array(
            'default' => 'html.png'
        ),

	    'limit_inline_size' => 1048576,

        /* Check for phishing exploits? */
        'phishing_check' => true
    )
// ...
```
