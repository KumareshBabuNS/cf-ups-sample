Pivotal Cloud Foundry -  User Provided Service Sample
================================

Introduction
------------

This is the Spring MVC sample application that can connect to a MySQL user provided service.  
This service is connected to by parsing the VCAP_SERVICES JSON and searching for a service name set as a property in the configuration of the "com.gopivotal.cf.workshop.cloudfoundry.MySQLUPSBasicDataSourceFactory" bean.  This application was modified from the Workshop application used for labs in the Pivotal CF Workshop.

###NOTE - THE README DOCUMENTATION IS INCOMPLETE AT THIS TIME

Building, Packaging, and Deploying
--------------------------------

###To get the source code and build the WAR file


    git clone https://github.com/aripka-pivotal/cf-ups-sample

    mvn clean package

###To run the application

This application leverages Spring profiles.


In the default and cloud profiles the application is set to use an embedded H2 database.
To take advantage of Pivotal CF's auto-configuration for services.  No
additional configuration is necessary when running locally or in Pivotal CF.

To leverage a user provided MySQL Service do the following:
    
 * set environment varaible to activate the mysql-ups profile

spring_profiles_active = mysql-ups

 * create and bind a user provided service pointing to a mysql database named cfw-ups-mysql


cf create-user-provided service mysql-ups
cf bind service 
 


