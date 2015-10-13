
HADOOP INSTALLATION INSTRUCTION
===============================
These installation instruction are for ubuntu/debian.

Version HADOOP : 2.7.0

1. Install jdk  
	 sudo apt-get install default-jdk
	 
2. sudo apt-get install ssh  
   sudo apt-get install rsync
   
3. ssh certificate setup  
   ssh-keygen -t dsa -P '' -f ~/.ssh/id_dsa  
   cat ~/.ssh/id_dsa.pub >> ~/.ssh/authorized_keys  
   
4. Install hadoop 2.7 from 
   
	   http://mirror.olnevhost.net/pub/apache/hadoop/common/hadoop-2.7.0/  
	   wget -c http://mirror.olnevhost.net/pub/apache/hadoop/common/hadoop-2.7.0/hadoop-2.7.0.tar.gz

5. After extracting it, move it to -  
	/usr/local/hadoop
   
6. Edit .bashrc file and added following lines- 

     	export JAVA_HOME=/usr/lib/jvm/java-7-openjdk-amd64
    	export HADOOP_HOME=/usr/local/hadoop
    	export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
    	export HADOOP_OPTS="-Djava.library.path=$HADOOP_HOME/lib"
    	export PATH=$PATH:$HADOOP_HOME/bin
    	export PATH=$PATH:$JAVA_HOME/bin
    	export PATH=$PATH:$HADOOP_HOME/sbin
    	export HADOOP_MAPRED_HOME=$HADOOP_HOME
    	export HADOOP_COMMON_HOME=$HADOOP_HOME
    	export HADOOP_HDFS_HOME=$HADOOP_HOME
    	export YARN_HOME=$HADOOP_HOME
    	export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
    	export HADOOP_OPTS="-Djava.library.path=$HADOOP_HOME/lib/native"
  	
7. Edited hadoop-env.sh file , added following lines-  
    export JAVA_HOME="/usr/lib/jvm/java-7-openjdk-amd64"

8. source ~/.bashrc

9. Edited following files and added lines -
    core-site.xml :-

	    <property>
	    	<name>fs.defaultFS</name>
	    	<value>hdfs://localhost:9000</value>
	    </property>
    
    hdfs-site.xml :-
    
	    <property>
	      <name>dfs.replication</name>
	      <value>1</value>
	      <description>Default block replication.
	      </description>
	    </property>
	    <property>
	      <name>dfs.name.dir</name>
	      <value>/home/amandeep/hadoop/data</value>
	    </property>
	    <property>
	      <name>dfs.data.dir</name>
	      <value>/home/amandeep/hadoop/dfs</value>
	    </property>

	yarn-site.xml :-

		<property>
			<name>yarn.nodemanager.aux-services</name>
			<value>mapreduce_shuffle</value>
		</property>

 mapred-site.xml :-
	
		<property>
			<name>mapreduce.framework.na	me</name>
			<value>yarn</value>
		</property>

10. sudo chown amandeep:amandeep -R /usr/local/hadoop

11. hdfs namenode -format

12. Start-all.sh to start file system.

13. Run following command to add directories in hdfs
		
		hdfs dfs -mkdir /user/
		hdfs dfs -mkdir /user/amandeep
		hdfs fs -chmod g+w /user/
		hdfs fs -chmod g+w /user/amandeep
