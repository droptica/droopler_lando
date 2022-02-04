# Droopler Lando
This repository provides with a lando configuration file for Droopler project.

# Running existing Droopler
Put the **.lando.yml** file in your project directory and run the following commands:
```bash
lando start
lando prepare
```
Import your database dump by running:
```bash
lando db-import dump.sql.gz
```
Update your **settings.php** file with the following database parameters:
* Host: database
* User: drupal9
* Database: drupal9
* Password: drupal9
* Port: 3306

```php
$databases['default']['default'] = [
  'database' => 'drupal9',
  'username' => 'drupal9',
  'password' => 'drupal9',
  'prefix' => '',
  'host' => 'database',
  'port' => '',
  'namespace' => 'Drupal\\Core\\Database\\Driver\\mysql',
  'driver' => 'mysql',
];
```
Don't forget to put public and private files into proper categories.

# Creating new Droopler installation
Please download or clone the [Droopler Project](https://github.com/droptica/droopler_project) skeleton and copy the [.lando.yml](.lando.yml) inside it. Then run the following commands:
```bash
lando start
lando build-profile
```

If you don't need the demo content, use the command `prepare` instead of `build-profile`, and run the Drupal install in the browser.

# Compiling frontend
* Please use `npm-theme` and `gulp-theme` commands to compile **droopler_theme**.
* Please use `npm-subtheme` and `gulp-subtheme` commands to compile **droopler_subtheme**.

```bash
lando npm-theme install
lando gulp-theme compile
lando gulp-theme dist
```
