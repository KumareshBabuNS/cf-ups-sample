Pivotal CF Workshop - Spring MVC - MYSQL - UserProvided Service
================================

Introduction
------------

This is the Spring MVC sample application for the Pivotal CF Workshop.
It is intended to demonstrate some of the basic functionality of Pivotal
CF (This spcific instance of the application has been modified to leverage a user provided service connection to a MYSQL instance):

 * Pivotal CF target, login, and push
 * Pivotal CF environment variables
 * Pivotal CF service variables
 * Scaling, router and load balancing
 * Health manager and application restart
 * RDBMS services via a UPS

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
 


