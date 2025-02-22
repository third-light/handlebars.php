Handlebars.php
==============
[![Build Status](https://travis-ci.org/XaminProject/handlebars.php.png?branch=master)](https://travis-ci.org/XaminProject/handlebars.php)
[![Scrutinizer Quality Score](https://scrutinizer-ci.com/g/XaminProject/handlebars.php/badges/quality-score.png?s=23a379f19b523498926eb3f2b60195815632e8ef)](https://scrutinizer-ci.com/g/XaminProject/handlebars.php/)
[![Code Coverage](https://scrutinizer-ci.com/g/XaminProject/handlebars.php/badges/coverage.png?s=9d6acd80ef2bda03cbd00a0cff35535614ce79ed)](https://scrutinizer-ci.com/g/XaminProject/handlebars.php/)
installation
------------

add the following to require property of your composer.json file:

`"xamin/handlebars.php": "dev-master"` for php 5.3+
`"xamin/handlebars.php": "dev-php-52"` for php 5.2

then run:

`$ composer install`

usage
-----

```php
<?php

// uncomment the following two lines, if you don't use composer
// require 'src/Handlebars/Autoloader.php';
// Handlebars\Autoloader::register();

use Handlebars\Handlebars;

$engine = new Handlebars;

echo $engine->render(
    'Planets:<br />{{#each planets}}<h6>{{this}}</h6>{{/each}}',
    array(
        'planets' => array(
            "Mercury",
            "Venus",
            "Earth",
            "Mars"
        )
    )
);
```

```php
<?php

use Handlebars\Handlebars;

$engine = new Handlebars(array(
    'loader' => new \Handlebars\Loader\FilesystemLoader(__DIR__.'/templates/'),
    'partials_loader' => new \Handlebars\Loader\FilesystemLoader(
        __DIR__ . '/templates/',
        array(
            'prefix' => '_'
        )
    )
));

/* templates/main.handlebars:

{{> partial planets}}

*/

/* templates/_partial.handlebars:

{{#each this}}
    <file>{{this}}</file>
{{/each}}

*/

echo $engine->render(
    'main',
    array(
        'planets' => array(
            "Mercury",
            "Venus",
            "Earth",
            "Mars"
        )
    )
);
```

contribution
------------

contributions are more than welcome, just don't forget to:

 * add your name to each file that you edit as author
 * use PHP CodeSniffer to check coding style.

