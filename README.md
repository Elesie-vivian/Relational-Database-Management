# Relational-Database-Management

This project takes a look at Amazon Relational Database to understand how database is set up and managed.

We navigate to the AWS search bar, input "RDS" to locate the RDs service
Navigate to the left sidebar and select the databases section, click on "create Database" to proceed with the following steps:

* Select Standard create Option

* Choose MySQL engine and proceed to complete the relevant fields;    choosing the name for the database as well as the master username .

* For this project we will use a VPC we created in our previous project and also an existing security group.

Note: We will edit security group inbound Rules and add an inbound rule for MySQL/Aurora on port 3306, allowing traffic from the 0.0.0.0/0 CIDR range.

* Choose an Availability zone, leave other settings as default and proceed to click the "create database" button. 


![alt text](<Images/Image 1.PNG>)

We will select the database created, under connectivity & security section, locate "Endpoint", copy the endpoint details and keep in a safe place for later use.

Next, we create an EC2 instance with an Amazon Linux image

![alt text](<Images/Image 2.PNG>)

After connecting to the instance , we run the following commands on the terminal to download and set up MySQL.

1. To Download the MySQL 5.7 Community Release Repository:

sudo wget https://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm

2. To Install the MySQL Repository Package:

sudo rpm -ivh mysql57-community-release-el7-11.noarch.rpm

3. To Import the GPG Key Manually:
sudo rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022

4. To Install MySQL 5.7:

sudo yum install mysql-community-server


![alt text](<Images/Image 3.PNG>)


5. We Start the MySQL Service Manually and Check Status Again:

sudo systemctl start mysqld.service
sudo systemctl status mysqld.service
sudo systemctl enable mysqld.service

We go further to connect our RDS to EC2 instance using the command:

mysql -h [Endpoint] -P [Port] -u-[Username] -p[Password]

![alt text](<Images/Image 4.PNG>)

To view all databases we run

SHOW DATABASES;

To use the database we have created, run

USE mysql;

To show tables inside the database run

SHOW TABLES;

![alt text](<Images/Image 5.PNG>)