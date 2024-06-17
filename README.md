# LEMP_STACK
### Introduction to the LEMP Stack

The LEMP stack is a powerful and popular set of open-source software used for web development, designed to host dynamic websites and applications. The acronym LEMP stands for Linux, Nginx (pronounced "Engine-X"), MySQL (or MariaDB), and PHP (or Python/Perl). Each component plays a crucial role in creating a robust, high-performing web server environment.

1. **Linux**: The foundation of the stack, Linux is a versatile and secure operating system that provides the necessary environment for running the other components. Its stability and extensive community support make it a preferred choice for hosting servers.

2. **Nginx**: Acting as the web server, Nginx is renowned for its high performance, stability, and low resource consumption. It efficiently handles multiple simultaneous connections, making it ideal for serving dynamic web content quickly and reliably.

3. **MySQL/MariaDB**: These relational database management systems (RDBMS) are used for storing and managing data. MySQL is one of the most widely used databases in the world, while MariaDB is a fork of MySQL that offers additional features and improved performance. Both are capable of handling large datasets and complex queries, providing a solid backend for data storage.

4. **PHP/Python/Perl**: These programming languages are used to create dynamic web content. PHP is the most common choice within the LEMP stack due to its simplicity and wide adoption. Python and Perl are also supported, offering developers flexibility in choosing the right language for their projects.

The LEMP stack is favored by developers for its flexibility, scalability, and efficiency. It's suitable for a wide range of applications, from small personal projects to large-scale enterprise solutions. By leveraging the strengths of each component, the LEMP stack provides a reliable and efficient environment for developing and deploying web applications.

## A journey through the LEMP_STACK 
## Prequisites:
1. AWS account 
2. Ec2 instane
3. GitBash
Connecting to the Ec2 instance through Gitbash
![onnecting to a aws vir through gitbash](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/82b825a9-8bcc-4d99-9655-d43efaa266c1)



## Step1(Installing Nginx Sever):
1
We first update then install Nginx server by using the code below 

__`sudo apt update`
`sudo apt install nginx`__

![installing nginx](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/659c5264-3728-409d-9717-7efd0ae3273d)

2
Verify that nginx was succesfully installed by using this code.

__`sudo systemctl status nginx`__

![iginx status](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/c15b092b-8ed2-4072-9001-0e501880a431)


3
Checking to see the sever can be accessed 

checking through ubuntu ClI first by 
` curl http://127.0.0.1:80 `

![access throu cli](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/8b999655-24d2-46e7-8209-8260feed1bde)

Checking through a browswer http://18.234.210.235:80

![nginx ob browser](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/ac09890b-8927-4ef1-b687-0c7f9dce62ad)


## Step2( Istallin MYSQL):

1
Install MYSQL with `sudo apt install mysql_sever`

![install msql](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/784b0f0d-240e-4ffb-a6eb-909c11611a0e)

2
Log into MySQL

![intosql](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/442d0ef7-5179-4d52-97c8-26b41f8bb94f)

3
Set a password for root User
`ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'theghost';`

![alterpass](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/0e8fc4ca-48c9-486f-bbbe-1f43fb239e4e)

4
Running a security script that removes some insecure default settings and lockdown access to your database
This script is done by this code 

`sudo mysql_secure_installation`
![securescript](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/13b9c26d-c054-4a34-bed4-af32a42029d1)

I left everything at default settings, apart from the password security level i choose low

5
Test if you are able to loggin MySQL:
```
sudo mysql -p
```
![verifysql](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/1ba14ae9-1e73-47e6-81b8-cf6e195a2ff2)


## Step3( INstalling PHP ):
Nginx requires an external program to handle PHP processing and act as a bridge between the PHP interpreter itself and the websever.
We will need to install php-fpm(PHP fastCGI process manager) and php-mysql( a module that help PHP to communicate with MySQL-based databases

```
sudo apt install php-fpm php-mysql
```
![phpinstall1](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/a55db6b7-7f7d-4769-9ec1-ce9b3f7a996d)

![phpinstall2](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/a8ec6bee-c9ef-4fb7-a915-40a225839e4d)


## Step4( Configuration of Nginx to use PHP processor ):
1
Create a root web directory for the Domain:
```
sudo mkdir /var/www/projectLEMP
```
2
Assign ownership of the directory with the $USER:
```
sudo chown -R $USER:$USER /var/wwww/projectLEMP
```
3
Create and open a in Nginx's sites-available:
```
sudo vim /etc/nginx/sites-available/projectLEMP
```
4
Then input the following code:
![inputthis](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/ce7153f4-c0f4-46d2-8f95-a3f59e1f54dc)

5
Activate your Configuration:
```
sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/
```
this will tell nginx to use the config next time reloaded.

6
Test your config:
```
sudo nginx -t
```
![testngin](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/64f0c665-d571-4c86-8285-3605fda7d69b)

Dissable default Nginx 
```
sudo unlink /etc/nginx/sites-enabled/default
```
Reload changes:
```
sudo systemctl reload nginx
```
create a file in /var/www/projectLEMP
```
sudo touch /var/www/projectLEMP/index.html
```
Test in your browser to see if config works perfectly
![workswell](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/10ca7a68-7d47-4385-848d-81a46177622b)
 This shows it works well 

## Step5 ( Testing PHP with Nginx ):
1
Validate if Nginx can correctly hand .php files off to your processor:
```
vim /var/www/projectLEMP/info.php
```
copy and paste 
![image](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/9ef6ef4a-4b79-4faa-9110-d332efe01070)

## step6 (Retrieving data from MySQL database with PHP):
1 
Connect to MySQl 
```
sudo mysql
```
2
create a new database 
```
CREATE DATABASE `example_database`;
```
![image](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/aa93dc9d-c5c2-43f7-a2f3-55fcb7111925)

3
New user 
```
CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 'theghost';
```
![image](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/f5885756-30c2-4910-8b9c-e64f1348cc5a)

4
Give the user permission the databse:
```
GRANT ALL ON example_database.* TO 'example_user'@'%';
```
OUTPUT 
```
mysql> GRANT ALL ON example_database.* TO 'example_user'@'%';
Query OK, 0 rows affected (0.01 sec)
```
Try to login again with custom user credentials you created:
```
mysql -u example_user -p
```
![image](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/b368de14-b59b-49fe-80e3-76adcb50f894)

then proceed with checking database with 
```
SHOW DATABASE;
```
![image](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/eadaf77d-1dc5-461f-b119-100860b4e133)

5
Create a table named todo_list:
```
CREATE TABLE example_database.todo_list (
mysql>    item_id INT AUTO_INCREMENT,
mysql>    content VARCHAR(225),
mysql>    PRIMARY KEY(item_id)
mysql> );
```
![image](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/8d3ebaa8-4b49-4343-8475-3b1eb8c7437b)

6
Insert into the database:
```
INSERT INTO todo_list (content) VALUES 
("My first important item"),
("My second item"),
("My third item");

```
To confirm we use:
```
SELECT * FROM example_database.todo_list;
```
![image](https://github.com/OlavicDev/LEMP_STACK/assets/124717753/11349d56-1f6a-4988-a090-bcb1b6af9c38)

7
Create a script that connects MySQL and PHP:
```
vim /var/www/projectLEMP/todo_list.php
```
Input this:
```
<?php
$user = "example_user";
$password = "theGHOST.1";
$database = "example_database";
$table = "todo_list";

try {
  $db = new PDO("mysql:host=localhost;dbname=$databse", $user, $password);
  echo "<h2>TODO</h2><ol>";
  foreach($db->query("SELECT content FROM $table") as $row) {
    echo "<li>" . $row['content'] . "</li>";
  }
  echo "</ol>";
} catch (PDOExecption $e) {
    print "Error!: " . $e->getMessage() . "<br/>";
    die();
}

```





