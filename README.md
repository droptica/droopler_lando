# Droopler Lando
This repository provides with a lando configuration file for Droopler project.

# Running existing Droopler
Put the **.lando.yml** file in your project directory:
```bash
wget https://raw.githubusercontent.com/droptica/droopler_lando/master/.lando.yml

# Optionally, change project name in the lando.yml file.
sed -i 's/droopler/myproject/' .lando.yml
```
Then run the following commands:
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
Please download or clone the [Droopler Project](https://github.com/droptica/droopler_project) skeleton. Then run the following commands inside:
```bash
wget https://raw.githubusercontent.com/droptica/droopler_lando/master/.lando.yml

# Optionally, change project name in the lando.yml file.
sed -i 's/droopler/myproject/' .lando.yml

lando start
lando build-full-profile
```

The `lando build-full-profile` command will install all features of Droopler, including d_blog, d_product and demo content. If you prefer a bare version instead, please use `lando build-bare-profile`.

For the custom installation, use the command `prepare` instead of `build-*-profile`, and run `/install.php` in the browser. Remember to use `database` instead of `localhost` as MySQL host.

# Compiling frontend
* Please use `npm-theme` and `gulp-theme` commands to compile **droopler_theme**.
* Please use `npm-subtheme` and `gulp-subtheme` commands to compile **droopler_subtheme**.

```bash
lando npm-theme install
lando gulp-theme compile
lando gulp-theme dist
```
# Troubleshooting
If you are getting timeouts from the advagg module, please go to the `/admin/config/development/performance/advagg/js-minify?advagg=0` page and change the JS minification method from `JShrink` to `JSqueeze`.
