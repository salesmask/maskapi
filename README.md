# PHP Rest API Framework

[![Build Status](https://travis-ci.org/badrinathmutkule/phprestapi.svg?branch=1.x)](https://travis-ci.org/badrinathmutkule/phprestapi)
[![Coverage Status](https://coveralls.io/repos/github/badrinathmutkule/phprestapi/badge.svg?branch=3.x)](https://coveralls.io/github/badrinathmutkule/phprestapi?branch=1.x)
[![Total Downloads](https://poser.pugx.org/badrinathmutkule/phprestapi/downloads)](https://packagist.org/packages/badrinathmutkule/phprestapi)
[![License](https://poser.pugx.org/badrinathmutkule/phprestapi/license)](https://packagist.org/packages/badrinathmutkule/phprestapi)

PHP Rest API is a PHP micro-framework that helps you quickly write simple yet powerful APIs.

## Installation

It's recommended that you use [Composer](https://getcomposer.org/) to install PHP Rest API.

```bash
$ composer require badrinathmutkule/phprestapi "^1.0"
```

This will install PHP Rest API and all required dependencies. PHP Rest API requires PHP 5.5.0 or newer.

## Usage

Create an index.php file with the following contents:

```php
<?php

require_once 'vendor/autoload.php';

$rest = new PHPRestFramework\Rest("routes.yaml");
$rest->serve();

```

Create routes.yaml file for defining your routes 

```yaml

- url: /hello/world
  method: get
  controller: User
  action: getGreetings
  auth: 
  validation: 

- url: /hello/world
  method: post
  controller: User
  action: getGreetings
  auth: 
  validation:

```



You may quickly test this using the built-in PHP server:
```bash
$ php -S localhost:8000
```

Going to http://localhost:8000/hello/world will now display -

```json
{
    "error": true,
    "code": 1000,
    "message": {
        "greetings": "Hello world"
    },
    "process_time": 0.0000086408
}
```
For more information on how to configure your web server, see the [Documentation].


## Generate swagger documentation for your apis 

```php

require_once 'vendor/autoload.php';

define('DEBUG_MODE', TRUE);

$swagger = new PHPRestFramework\Swagger();

$swagger->set_info([
    "version" => "1.0",
    "title" => "Test APIs",
    "description" => "Your api description goes here.",
    "license" => [
        "name" => "MIT",
        "url" => "http://github.com/gruntjs/grunt/blob/master/LICENSE-MIT"
    ]
]);

$swagger->set_host("localhost:8080");
$swagger->set_base_path("/");  
$swagger->set_schema("HTTP"); //htttp or https 
$swagger->set_route_file('routes.yaml'); //route file path
$swagger->generate('wwwroot/doc/swagger.json');

```
## Tests

To execute the test suite, you'll need phpunit.

```bash
$ phpunit
```

## Security

If you discover security related issues, please email badrinath.mutkule@gmail.com instead of using the issue tracker.

## Credits

- [Badrinath Mutkule](https://github.com/badrinathmutkule)

## License

The PHP Rest API Framework is licensed under the MIT license. See [License File](LICENSE.md) for more information.
