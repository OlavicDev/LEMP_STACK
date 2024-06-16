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








