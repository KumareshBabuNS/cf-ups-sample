Pivotal Cloud Foundry -  User Provided Service Sample
================================

Introduction
------------

This project is a sample application written using Spring MVC that can connect to a MySQL user provided service. Here are the details of how this works: 

 * The service connection details are obtained by parsing the VCAP_SERVICES JSON
 * A specific service name is searched for, this is set as a property on the "com.gopivotal.cf.workshop.cloudfoundry.MySQLUPSBasicDataSourceFactory" bean.  

This application was modified from the Workshop application used for labs in the Pivotal CF Workshop. It contains all the same functionality, with the added addition of the ability to connect to a user provided MySQL instance.


Building, Packaging, and Deploying
--------------------------------

###To get the source code and build the WAR file


    git clone https://github.com/aripka-pivotal/cf-ups-sample

    mvn clean package

###To run the application

This application leverages Spring profiles to support both local and cloud deployment. 

 * In the default and cloud profiles the application is set to use an embedded H2 database.
 * The schema and sample data are auto loaded into the provided database if not already present.
 * The default data source will be auto reconfigured by Java builpack when the Java build pack can recognize the bound service is of type MySQL. No additional configuration is necessary.

**To leverage a user provided MySQL Service do the following:**

(All of the following instructions assume an application name of *sample-ups-app* Change app name as appropriate for you use)
    
 * set spring_profiles_active environment varaible to activate the mysql-ups profile

    ```cf set env sample-ups-app spring_profiles_active mysql-ups```

 * create and bind a user provided service pointing to a mysql database named cfw-ups-mysql

    ```cf create-user-provided-service sample-ups-db -p '{"URL":"jdbc:mysql://databasehost:3306/database", "USER":"someuser", "PASSWD":"somepass"}'```

    ```cf bind-service sample-ups-app sample-ups-db```

 * restart application to take advantage of the new database
