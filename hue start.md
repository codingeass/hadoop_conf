Tools to run before starting hue and there instruction:-  
As per installation and changes in .bashrc file run following commands.

1. Start Hadoop namenode, secondary node and data node  
    start-all.sh

2. Start oozie  
           	cd oozie/bin/  
            ./oozied.sh start
3. Start Spark   
       cd spark/sbin  
       start-master.sh 
4. Start livy server  
	     cd $HUE_HOME/apps/spark/java  
 	     ./bin/livy-server
 	     
5. Start hive server  
	hive --service hiveserver2
	
6. Start hue  
	hue runserver
