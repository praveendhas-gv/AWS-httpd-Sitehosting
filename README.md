# **Deploying a web application using Apache httpd on Cloud, AWS EC2 Instance.**

This project is to host a web application written in html using Apache httpd server

## **Setting up project environment** 

Initializing EC2 Instance. 
Log into AWS console using IAM User account. 
Create an EC2 instance
Select an OS image - Ubuntu
Create a new key pair with any name & download .pem file
Use the same key pair in the EC2 instance creation screen. 
Instance type - t2.micro
Connecting to the instance using ssh

Use the below command to connect to EC2 instance using SSH

```
ssh -i <keypair_name>.pem ubunutu@<IP_ADDRESS>
```

## **Configuring Ubuntu on EC2 instance and installing dependencies**

Update the outdated packages and dependencies. 

```
sudo apt update
```

Installing Git. 

Install git using the below command. 

```
sudo apt install git
```

Installing Apache HTTPD

```
sudo apt install apache2
sudo systemctl start apache2

```
The command sudo systemctl start apache2 starts the Apache service in Linux

## **Cloning source code into Ubuntu EC2 instance**

To obtain the source code, use the below git command to clone the git repository. 

```
git clone https://github.com/praveendhas-gv/AWS-httpd-Sitehosting.git
```

This will download all the contents of the repository AWS-httpd-Sitehosting and store it in the EC2 instance in the present working directory.

 
## **Hosting the application using Apache**
To host the application using Apache, copy the contents of the local git repository into the folder /var/www/html

From the same directory in which you executed the git clone command, use the below command to copy the files into the html folder

```
cp -r . /var/www/html
```

## **Accessing the application**

Apache listens on port 80
So the application can be accessed using the below link 

```
http://<ec2-instance-public-ip>:80/
```

If the link is inaccessible, it could mean either the security group does not allow inbound http traffic or the apache2 service is not running.

To check the status of apache2 service, use the following command

```
sudo systemctl status apache2
```
If the service is not running, start the service. 

If the security group is not allowing inbound http traffic, go to the inbound rules in the security group and allow http traffic

