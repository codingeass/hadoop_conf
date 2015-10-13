Pig Installation Instruction
============================

1. Download pig from http://mirror.cc.columbia.edu/pub/software/apache/pig/pig-0.14.0/pig-0.14.0.tar.gz

2. Extract it by typing  
    tar -zxvf pig-0.14.0.tar.gz

3. Move it to location   
    /home/amandeep/
	  mv pig-0.14.0 /home/amandeep

4. Add following lines to bashrc file -	

    	export PIG_INSTALL=/home/amandeep/pig-0.14.0
    	export PATH=$PATH:$PIG_INSTALL/bin

5. Run  
	source ~/.bashrc

6. Add configuration files of hadoop by moving core-site.xml,hdfs-site.xml and mapred-site.xml to pig-0.14.0/conf
