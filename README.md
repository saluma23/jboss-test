# jboss-test
developer-forum.war -> jboss -> mysql

sudo podman run -d --name jboss -p 8080:8080 -p 9990:9990 -p 8443:8443 daggerok/jboss-eap-7.3:7.3.0-centos

sudo podman run -d --name mysql -p 3306:3306 -e MYSQL_ALLOW_EMPTY_PASSWORD=yes mysql 

suso podman exec -it mysql /bin/bash

mysql -uroot

create database employees;

use employees;

CREATE TABLE `employee` (
  `id` int NOT NULL AUTO_INCREMENT,
  `first_name` varchar(20) DEFAULT NULL,
  `last_name` varchar(20) DEFAULT NULL,
  `username` varchar(250) DEFAULT NULL,
  `password` varchar(20) DEFAULT NULL,
  `address` varchar(45) DEFAULT NULL,
  `contact` varchar(45) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

sudo podman inspect mysql --format="{{.NetworkSettings.IPAddress}}"

Eclipse:
--------
use the IP address in our application. (src\main\java\com\salman\dao\Employeedao.jsp)

File -> save all

export -> war

upload to git -> saluma23/jboss-test

browser:
--------
localhost:8080

admin console: 

user: admin

password: Admin.123

deployment -> deploy war

localhost:8080/developer-forum/register

Notes:
------
Runtimes:
App is using JAVA JRE - 1.8

Container JBOSS (daggerok/jboss-eap-7.3:7.3.0-centos) is using openjdk-1.8 (supports all versions of JAVA JRE 1.8)

MYSQL:
IP Address of the container is found using (podman inspect mysql --format="{{.NetworkSettings.IPAddress}}")

map it to our application source code of java jdbc connection jsp program.
 
