# EmailValidator

## Suported RFCs ##
This library aims to support:

RFC 5321, 5322, 6530, 6531, 6532.

## Requirements ##

 * [Composer](https://getcomposer.org) is required for installation
 * [Spoofchecking](https://github.com/egulias/EmailValidator/blob/master/EmailValidator/Validation/SpoofCheckValidation.php) and [DNSCheckValidation](https://github.com/egulias/EmailValidator/blob/master/EmailValidator/Validation/DNSCheckValidation.php) validation requires that your PHP system has the [PHP Internationalization Libraries](https://php.net/manual/en/book.intl.php) (also known as PHP Intl)

## Installation ##

Run the command below to install via Composer

```shell
composer require jeronimofagundes/email-validator "dev-master"
```
Optional 
You must install php-dig to perform DNS Dig Validation
```shell
composer require jeronimofagundes/php-dig "dev-master"
```

## Getting Started ##
`EmailValidator`requires you to decide which (or combination of them) validation/s strategy/ies you'd like to follow for each [validation](#available-validations).

A basic example with the RFC validation
```php
<?php

use Egulias\EmailValidator\EmailValidator;
use Egulias\EmailValidator\Validation\RFCValidation;

$validator = new EmailValidator();
$validator->isValid("example@example.com", new RFCValidation()); //true
```


### Available validations ###

1. [RFCValidation](https://github.com/egulias/EmailValidator/blob/master/EmailValidator/Validation/RFCValidation.php)
2. [NoRFCWarningsValidation](https://github.com/egulias/EmailValidator/blob/master/EmailValidator/Validation/NoRFCWarningsValidation.php)
3. [DNSCheckValidation](https://github.com/egulias/EmailValidator/blob/master/EmailValidator/Validation/DNSCheckValidation.php)
4. [DNSDigCheckValidation](https://github.com/jeronimofagundes/EmailValidator/blob/master/EmailValidator/Validation/DNSDigCheckValidation.php)
5. [GMailValidation](https://github.com/jeronimofagundes/EmailValidator/blob/master/EmailValidator/Validation/GMailValidation.php)
6. [HotmailValidation](https://github.com/jeronimofagundes/EmailValidator/blob/master/EmailValidator/Validation/HotmailValidation.php)
7. [SpoofCheckValidation](https://github.com/egulias/EmailValidator/blob/master/EmailValidator/Validation/SpoofCheckValidation.php)
8. [MultipleValidationWithAnd](https://github.com/egulias/EmailValidator/blob/master/EmailValidator/Validation/MultipleValidationWithAnd.php)
9. [Your own validation](#how-to-extend)

`MultipleValidationWithAnd`

It is a validation that operates over other validations performing a logical and (&&) over the result of each validation.

```php
<?php

use Egulias\EmailValidator\EmailValidator;
use Egulias\EmailValidator\Validation\DNSCheckValidation;
use Egulias\EmailValidator\Validation\MultipleValidationWithAnd;
use Egulias\EmailValidator\Validation\RFCValidation;

$validator = new EmailValidator();
$multipleValidations = new MultipleValidationWithAnd([
    new RFCValidation(),
    new DNSCheckValidation()
]);
$validator->isValid("example@example.com", $multipleValidations); //true
```

### How to extend ###

It's easy! You just need to implement [EmailValidation](https://github.com/egulias/EmailValidator/blob/master/EmailValidator/Validation/EmailValidation.php) and you can use your own validation.


## Other Contributors ##
(You can find current contributors [here](https://github.com/jeronimofagundes/EmailValidator/graphs/contributors))

As this is a port from another library and work, here are other people related to the previous one:

* Ricard Clau [@ricardclau](https://github.com/ricardclau):      	Performance against PHP built-in filter_var
* Josepf Bielawski [@stloyd](https://github.com/stloyd):      		For its first re-work of Dominic's lib
* Dominic Sayers [@dominicsayers](https://github.com/dominicsayers):  	The original isemail function

## License ##
Released under the MIT License attached with this code.

