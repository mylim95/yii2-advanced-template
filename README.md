<p align="center">
    <a href="https://github.com/yiisoft" target="_blank">
        <img src="https://avatars0.githubusercontent.com/u/993323" height="100px">
    </a>
    <h1 align="center">Yii 2 Advanced Project Template</h1>
    <br>
</p>

Yii 2 Advanced Project Template is a skeleton [Yii 2](http://www.yiiframework.com/) application best for
developing complex Web applications with multiple tiers.

The template includes three tiers: front end, back end, and console, each of which
is a separate Yii application.

The template is designed to work in a team development environment. It supports
deploying the application in different environments.

Documentation is at [docs/guide/README.md](docs/guide/README.md).

[![Latest Stable Version](https://img.shields.io/packagist/v/yiisoft/yii2-app-advanced.svg)](https://packagist.org/packages/yiisoft/yii2-app-advanced)
[![Total Downloads](https://img.shields.io/packagist/dt/yiisoft/yii2-app-advanced.svg)](https://packagist.org/packages/yiisoft/yii2-app-advanced)
[![Build Status](https://travis-ci.org/yiisoft/yii2-app-advanced.svg?branch=master)](https://travis-ci.org/yiisoft/yii2-app-advanced)

Installation
-------------------
>I am assuming that you know how to: install and use Composer, and install additional packages/drivers that may be needed for you to run everything on your system. In case you are new to all of this, you can check my guides for installing default yii2 application templates, provided by yii2 developers, on Windows 8 and Ubuntu based Linux operating systems, posted on www.freetuts.org.

1. Create database that you are going to use for your application (you can use phpMyAdmin or any
other tool you like).

2. Now open up your console and ```cd``` to your web root directory, 
for example: ``` cd /var/www/sites/ ```

3. Run the Composer ```create-project``` command:

   ``` composer create-project mylim95/yii2-advanced-template.git ```
   
   3a.Or you can using gir clone commnad: ```git clone https://github.com/mylim95/yii2-advanced-template.git```

4. Once template is downloaded, you need to initialize it in one of two environments:
development (dev) or production (prod). Change your working directory to ```_protected``` 
and execute ```php init``` command.

   ```cd advanced/_protected/```

   ```php init ```

   Type __0__ for development, execute coomant, type __yes__ to confirm, and execute again.

5. Now you need to tell your application to use database that you have previously created.
Open up main-local.php config file in ```advanced/_protected/common/config/main-local.php``` 
and adjust your connection credentials.

6. Back to the console. It is time to run yii migrations that will create necessary tables in our database.
While you are inside ```_protected``` folder execute ```./yii migrate command```:

   ``` ./yii migrate ``` or if you are on Windows ``` yii migrate ```

7. Execute _rbac_ controller _init_ action that will populate our rbac tables with default roles and
permissions:

   ``` ./yii rbac/init ``` or if you are on Windows ``` yii rbac/init ```

You are done, you can start your application in your browser.

__*Tip__: if your application name is, for example, __advanced__, to see the frontend side of it you 
just have to visit this url in local host: ```localhost/advanced```. To see backend side, this is 
enough: ```localhost/advanced/backend```.

> Note: First user that signs up will get 'The Creator' (super admin) role. This is supposed to be you. This role have all possible super powers :) . Every other user that signs up after the first one will get 'member' role. Member is just normal authenticated user. 

Testing
-------------------

If you want to run tests you should create additional database that will be used to store 
your testing data. Usually testing database will have the same structure like the production one.
I am assuming that you have Codeception installed globally, and that you know how to use it.
Here is how you can set up everything easily:

1. Let's say that you have created database called ```advanced```. Go create the testing one called    ```advanced_tests```.

2. Inside your ```main-local.php``` config file change database you are going to use to ```advanced_tests```.

3. Open up your console and ```cd``` to the ```_protected``` folder of your application.

4. Run the migrations again: ``` ./yii migrate ``` or if you are on Windows ```yii migrate```

5. Run rbac/init again: ``` ./yii rbac/init ``` or if you are on Windows ```yii rbac/init```

6. Now you can tell your application to use your ```advanced``` database again instead of ```advanced_tests```.
Adjust your ```main-local.php``` config file again.

7. Now you are ready to tell Codeception to use ```advanced_tests``` database.
   
   Inside: ``` _protected/tests/codeception/config/config.php ``` file tell your ```db``` to use 
   ```advanced_tests``` database.

8. Start your php server inside the root of your application: ``` php -S localhost:8080 ``` 
(if the name of your application is advanced, then root is ```advanced``` folder) 

9. To run tests written for frontend side of your application 
   ```cd``` to ```_protected/tests/codeception/frontend``` , run ```codecept build``` and then run your tests.

10. Take similar steps like in step 9 for backend and common tests.


DIRECTORY STRUCTURE
-------------------

```
common
    config/              contains shared configurations
    mail/                contains view files for e-mails
    models/              contains model classes used in both backend and frontend
    tests/               contains tests for common classes    
console
    config/              contains console configurations
    controllers/         contains console controllers (commands)
    migrations/          contains database migrations
    models/              contains console-specific model classes
    runtime/             contains files generated during runtime
backend
    assets/              contains application assets such as JavaScript and CSS
    config/              contains backend configurations
    controllers/         contains Web controller classes
    models/              contains backend-specific model classes
    runtime/             contains files generated during runtime
    tests/               contains tests for backend application    
    views/               contains view files for the Web application
    web/                 contains the entry script and Web resources
frontend
    assets/              contains application assets such as JavaScript and CSS
    config/              contains frontend configurations
    controllers/         contains Web controller classes
    models/              contains frontend-specific model classes
    runtime/             contains files generated during runtime
    tests/               contains tests for frontend application
    views/               contains view files for the Web application
    web/                 contains the entry script and Web resources
    widgets/             contains frontend widgets
vendor/                  contains dependent 3rd-party packages
environments/            contains environment-based overrides
```
