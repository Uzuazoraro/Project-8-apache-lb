# LOAD BALANCER SOLUTION WITH APACHE

We'll start by creating one new AWS EC2 Instance.This will be used as a load balancer. Then we'll also make use of the webservers we created in project 7.

![Creation of EC2 Instance](./EC2 Instance created)

Add port 80 to Instance security group.

- Install Apache Load Balancer on Project-8-apache-lb server and configure it to point traffic coming to LB to both Web Server.

Install Apache:

Update Ubuntu with this command:
`sudo apt update`

![Update ubuntu](./Ubuntu updated)

Upgrade ubuntu with this command:
`sudo apt upgrade`

`sudo apt install apache2 -y`

![Apache installed](./Installing Apache2)

`sudo apt-get install libxml2-dev`

![Apche utilities](./Building apache dependencies)

`sudo apt-get install libxml2-dev`
Use to build apache packets and dependencies.

![Apche utilities](./apache dependencies)

- Enable following modules

`sudo a2enmod rewrite`
`sudo a2enmod proxy`
`sudo a2enmod proxy_balancer`
`sudo a2enmod proxy_http`
`sudo a2enmod headers`
`sudo a2enmod lbmethod_bytraffic`

![Modules enabled](./enabling apache modules)

- Restart apache2 service

`sudo systemctl restart apache2`

- Confirm the status of apache2

`sudo systemctl status apache2`

![To confirm apache status](./apache is active and running)

- Configure load balancing

`sudo vi /etc/apache2/sites-available/000-default.conf`
This is used to open apache file to enable configuration.

![Apache file to be configured](./apache configuration file)

Upload proxy from the document and paste in the file. Then copy the private IP address of werserver1 and webserver2 and put them in the appropriate sections.

![apache file has been updated](./updated file)

- Restart apache server

`sudo systemctl restart apache2`

Verify that our configuration works – try to access your LB’s public IP address or Public DNS name from your browser:

![Confirmed config works](./load balancer verification)
