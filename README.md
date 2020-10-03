# PHP-CS-Fixer Docker Development Environment  
  
This repository contains a Docker Compose configuration to support development within the [FriendsOfPHP/PHP-CS-Fixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer) project.   
   
It provides a php-fpm image wiith the necessary PHP extensions for PHP-CS-Fixer development, and installs composer. php-fpm is chosen to allow for integration with IDEs that can execute PHP on remote servers.  

*Experience with Docker and Docker Compose is assumed.*
   
## Supported PHP Versions  
  
* PHP 8.0.0RC1  
  
I created this configuration to aid in supporting PHP 8 compatibility, so that is the only language version available at this time.  
  
## Usage  
  
Create a file named `.env` at the root of your project and set the `PHP_CS_FIXER_PROJECT_DIR` variable, which should  
be the path to your local PHP-CS-Fixer project. Example:  
  
```  
PHP_CS_FIXER_PROJECT_DIR=../PHP-CS-Fixer  
```  
  
Run `docker-compose build php8` to build the php8 image.  **You should rebuild the image whenever this project has updates.**  
  
Run `docker-compose up php8` to start the php-fpm container.  
  
### Running composer  
  
This configuration will host-mount your composer vendor directory (using a new performance enhancement for Docker for Mac). You may wish to run composer in the container to test it with PHP 8. Use the `--ignore-platform-reqs` option to skip errors about unsupported PHP versions.  You may also want to clear out your vendor directory and composer lock file.  
 
```  
docker-compose exec php8 composer install --ignore-platform-reqs  
```  
  
### Running tests  
  
```  
docker-compose exec php8 vendor/bin/phpunit  
```  
  
## Issues and Contributing  
  
Please report any issues in GitHub's issue tracker. Contributions are welcome!  
  
[Andrew Hoffmann](mailto:andrew.hoffmann.wi@gmail.com) - @hamdrew
