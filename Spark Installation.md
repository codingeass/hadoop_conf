Spark Installation Instruction
==============================
Version 1.4.0

1. Download Spark from https://spark.apache.org/downloads.html

2. Select package type :   
    Pre-built for Hadoop 2.6 and later

3. After extracting paste it to you home directory with folder name spark

4. Add following line in .bashrc

    	export SPARK_HOME=/home/amandeep/spark
    	export PATH=$PATH:$SPARK_HOME/bin

5. Run source ~/.bashrc

6. Start a standalone master server by executing: 

       ./sbin/start-master.sh
