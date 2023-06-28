# LAMP-Stack

![image](https://user-images.githubusercontent.com/63364609/225725286-14046a95-d6e7-42a2-9345-35c714604acd.png)

Installation of LAMP stack on Amazon Linux OS on AWS Ec2 Instance
 
LAMP is a software stack that is widely used for building and hosting dynamic web applications. It offers a low cost of ownership, easy customization, and a large user community. The components of the LAMP stack are highly compatible and can be easily integrated, making it a popular choice for web developers.

The acronym stands for Linux, Apache, MySQL, and PHP. Let's look at each component in detail:

Linux: Linux is an open-source operating system that is widely used for web hosting purposes. It provides a stable, secure, and scalable environment for web applications to run. Linux is flexible and can be easily configured to meet the requirements of different web applications.

Apache: Apache is a widely used open-source web server software that serves HTTP requests and manages the flow of data between the client and server. It is highly configurable, with a large number of modules that can be added to extend its functionality. Apache is also highly scalable, and can handle a large number of concurrent connections, making it suitable for high-traffic web applications.

MySQL: MySQL is an open-source relational database management system (RDBMS) that is used to store and retrieve data in a structured manner. It is widely used in web applications due to its reliability, scalability, and ease of use. MySQL provides a high level of security, with built-in encryption and access control mechanisms to ensure the protection of sensitive data.

PHP: PHP is a server-side scripting language that is used to write dynamic web pages and applications. PHP code is executed on the server, and the results are sent back to the client in the form of HTML or other formats. PHP provides a large number of functions and libraries that make it easy to perform tasks such as accessing databases, generating dynamic content, and handling user input.

Step 1: Creating an Amazon Linux OS in AWS Ec2 Instance

![image](https://user-images.githubusercontent.com/63364609/225725385-7a96552f-8fdd-4da0-bac1-3c1ef855ad12.png) 
Create AWS account and search Ec2 in search bar and click on Launch Instance.

![image](https://user-images.githubusercontent.com/63364609/225725484-17109b9d-a481-49aa-abc5-e5ae62622aa7.png)
Creating a Ec2 instance with Amazon Linux OS , naming it LAMP instance 

![image](https://user-images.githubusercontent.com/63364609/225725568-58bb8209-ae69-4ea9-b380-8d83669b4216.png)
Create a key pair and in network settings allow HTTP traffic then click on launch instance.

Step 2 : Install and Run Apache (httpd) in Amazon Linux OS
“httpd” is Apache package name in Amazon linux, whereas in ubuntu OS it is called as “apache2”

Commands need to be run.
sudo yum install httpd -y
sudo service httpd start
sudo service httpd status

![image](https://user-images.githubusercontent.com/63364609/225725731-946adc08-46d5-43fb-9010-aee41d47695e.png)
Apache install and started successfully. A part is completed for LAMP stack.

Step 3 : Install and Run mysql in Amazon Linux OS
Latest Upgraded version of Mysql is called Mariadb. we can say that mysql and mariadb both are same above mysql version 5.8 and in Amazon Linux 2 mysql is available as “mariadb-server”.

Commands need to be run.
sudo yum install mariadb-server -y 
sudo service mariadb start
sudo service mariadb status

![image](https://user-images.githubusercontent.com/63364609/225725890-01200032-351b-476c-a2b9-f36071c4eb51.png)
 Mariadb install and running successfully. we also need to set password for it. 

Command to set a password for it to make it more secure 
sudo mysql_secure_installation

![image](https://user-images.githubusercontent.com/63364609/225725959-cd2a0d0e-727c-40f0-9af9-79a557ef5d05.png)

it asks for current password , just press ENTER on keyboard as its not having any password

![image](https://user-images.githubusercontent.com/63364609/225726018-fb937bd8-5347-4cb7-ab20-42e1ba2157dc.png)

Now it asks for setting root password , say yes ( press y) and enter new password , root is default usern name in mysql/mariadb while entering password cursor does not moves , so still enter password.

![image](https://user-images.githubusercontent.com/63364609/225726034-66e28361-cccb-4990-a192-4e11ec629afc.png)

Now, it will ask some questions like do you want to remove anonymous users? , Disallow root login remotely? etc.. press y until it finishes and tells Thanks for using mariaDB.

Now you can login to mysql/mariadb by running below command
mysql -u root -p

![image](https://user-images.githubusercontent.com/63364609/225726062-1b1d4cdb-0789-45a0-a283-2c4793400d76.png)

Enter password which you have set in above steps, you have successfully connected to mariadb. To check databases details run command show databases; .  To exit from mariadb entire exit and press enter. M part is completed for LAMP stack.
Step 4 : Install and Run php in Amazon Linux OS
To install php in amazon linux OS packet manage is amazon-linux-extras and php8.0 is it will install php version of 8.0
Commands need to be run.
sudo amazon-linux-extras install php8.0  -y
sudo service php-fpm start
sudo service php-fpm status

![image](https://user-images.githubusercontent.com/63364609/225726109-f34859f0-d40e-4e8c-ab72-03ce449c291b.png)
 
Php is install and running successfully. 
Now go to apache web server directory using its default path /var/www/html and create a php file called index.php to test our php installation and its working.
Commands to run
cd /var/www/html/
sudo nano index.php 

![image](https://user-images.githubusercontent.com/63364609/225726141-18644631-7d61-4702-9b9d-3ee0fa9fc858.png)
 
Gone to html directory and create a php file

![image](https://user-images.githubusercontent.com/63364609/225726176-92c9d85e-0f57-47b5-8fc1-f11450b1b704.png)

Added some content in index.php file. M part is completed for LAMP stack.
Now once restart all services using below commands 
sudo service httpd restart
sudo service mariadb restart
sudo service php-fpm restart

![image](https://user-images.githubusercontent.com/63364609/225726213-0385d31d-a397-4cac-9322-8f5a1fbc0d19.png)
 
Now, copy public IP of your Ec2 instance and past it in web-browser with index.php path.
http://43.205.216.136/index.php  
 
![image](https://user-images.githubusercontent.com/63364609/225726243-47170e0f-94a8-40f6-8a02-9682edc282c6.png)

Yeappp..! LAMP stack is installed successfully and php page is running successfully.

