# self-hosted disposable email system

This disposable email solution can be hosted on your own standard PHP-webhoster. All you need is PHP with mailparse extension and "Pipe to a Program" functionality. The system is as simple as possible, with minimal codebase and complexity. 

## Usage
When accessing the web-app a random email address is generated for you. The page will reload until emails have arrived. You can delete emails and see the original sourcecode. 


## Licence
Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)

https://creativecommons.org/licenses/by-nc/4.0/

## Requirements

* PHP, Version 5.3.0
* Apache 2
* [mailparse extension](http://pecl.php.net/package/mailparse)
* [Composer](https://getcomposer.org/doc/00-intro.md#globally) (PHP Package Manager)

## Installation

* Clone this repository
* Download dependencies: 

		cd path/to/project/src
		composer install

* Create a symlink from the ``htdocs`` to the ``public`` directory: ``cd /var/www/html; ln -s /path/to/disposable-email/public mail`` 
    
- assure the mailparse extension is installed. The following command should not print any error: 
  
        <?php mailparse_msg_create(); ?>

## Configuration
- forward/pipe e-mail to the php script `app/pipe_input.php` (e.g.  [cpanel](https://documentation.cpanel.net/display/ALD/Forwarders#Forwarders-PipetoaProgram) docs)
- (optionally) configure a different database like mysql in `app/config.php`
 
## TODO
 1. security audit against xss/sqli
 1. simplify installation: zero-config

## development environment
There is a Vagrantfile to be used with [vagrant](https://www.vagrantup.com/). 

### OSX dependencies 
- install php: https://github.com/Homebrew/homebrew-php
- add php to path: fish config: `set PATH /usr/local/opt/php55/bin $PATH`
-  `pecl install mailparse`
- (see "php --ini" for file: ) `echo "extension=mailparse.so" >> /usr/local/etc/php/5.5/php.ini`

## See also
 - inspired by script: https://github.com/moein7tl/TempMail/blob/master/web/index.php
     

