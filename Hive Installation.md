1. Download hive from -  
    http://apache.claz.org/hive/stable/apache-hive-1.2.0-bin.tar.gz

2. After extracting, copying files to /usr/local/hive/  
    sudo mv apache-hive-1.2.0-bin /usr/local/hive

3. Edit .bashrc file by appending following lines-  

      	export HIVE_HOME=/usr/local/hive
      	export PATH=$PATH:$HIVE_HOME/bin
      	export CLASSPATH=$CLASSPATH:/usr/local/Hadoop/lib/*:.
      	export CLASSPATH=$CLASSPATH:/usr/local/hive/lib/*:.

4. Execute .bashrc  
    source ~/.bashrc

5. Edit hive-env.sh file by appending lines     
	export HADOOP_HOME=/usr/local/hadoop

6. Enable the lock manager by setting properties in /etc/hive/conf/hive-site.xml   

		<property>
		  <name>hive.support.concurrency</name>
		  <description>Enable Hive's Table Lock Manager Service</description>
		  <value>true</value>
		</property>


7. Running following line in hdfs-
 
		hadoop fs -mkdir /tmp 
		hadoop fs -mkdir /user/hive/warehouse
		hadoop fs -chmod g+w /tmp 
		hadoop fs -chmod g+w /user/hive/warehouse

8. Run  hive by typing -   
        hive
