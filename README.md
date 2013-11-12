url-shortener
=============

Test application "URL shortener"
This appication was made according to test task http://www.xiag.ch/testtask/ and 
recomendations http://blog.xiag.ru/2012/10/reminder-for-candidates.html


Application was created from the scratch during 2 evenings.
* MVC patten (see AppController.php, AppForm.php, AppModel.php, AppView.php)
* ORM-like database access (see AppDbConnection.php, ApModel.php)
* MVVM pattern (see AppForm.php)
* Configurable components
* AJAX on native javascript





REQUIREMENTS:
PHP 5.3, MYSQL 5.5, NGINX, PHP-FPM


INSTALLATION:

-- 1. install software (for debian/ubuntu)
>$ sudo apt-get install php5 php5-fpm nginx php5-mysql mysql-client-core-5.5 mysql-server


-- 2. may need some manual configuration ...



-- 3. create new mysql database
-- see http://www.mysql.ru/docs/man/CREATE_DATABASE.html
for example create database named 'url'
>$ mysql -u{adminLogin} -p{adminPassword}
>mysql shell
> CREATE DATABASE IF NOT EXISTS `url`;
> QUIT;


-- 4. create new user
-- see http://www.mysql.ru/docs/man/Adding_users.html
for example create user named 'url_rw' with password 'user-password'
>$ mysql -u{adminLogin} -p{adminPassword}
>mysql shell
> USE `url`;
> GRANT ALL PRIVILEGES ON *.* TO url_rw@localhost IDENTIFIED BY 'user-password';
> QUIT;


-- 5. prepare directory for web application
>$ sudo mkdir -p /var/www/url.com
>$ sudo chown -R nginx:www-data /var/www/url.com


-- 6. download web application (need account at github.com)
>git clone git@github.com:pvolyntsev/url-shortener.git /var/www/url


-- 7. register web applicatio in nginx
>sudo ln -s /var/www/url.com/app/config/url.com.conf /etc/nginx/sites-enabled/
>sudo /etc/init.d/nginx reload


-- 8. load database dump
>for example
>$ mysql -u{adminLogin} -p{adminPassword} {databaseName} < /var/www/url.com/dump_url.sql


-- 9. add this line into /etc/hosts
>127.0.0.1 dev-url.com url.com
--    if you use virtual machine to run application, add the same line into 'hosts'
--    file at your host machine, with other IP address


-- 10. open http://dev-url.com/ in browser
