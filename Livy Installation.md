Livy Spark Server Installation
==============================

1. To build, run :

  	cd $HUE_HOME/apps/spark/java  
  	mvn -DskipTests clean package

2. Running tests :

  	cd $HUE_HOME/apps/spark/java
  	mvn test

3. Running livy server

   	./bin/livy-server
