Oozie Installation
==================

1. Download oozie from  
    http://apache.mirrors.ionfish.org/oozie/4.2.0/oozie-4.2.0.tar.gz

2. Download extjs file 2.2.0 version  

3. Edit pom.xml file directly in oozie-4.2.0 , edit version of hadoop for profile with id "hadoop-2" . Also edit pig and hive version.

4. Run command-  
    ./bin/mkdistro.sh -DskipTests -Dhadoopversion=2.7.0 -DjavaVersion=1.7 -DpigVersion=0.14.0 -Dhiveversion=1.2.0

5. Make separate folder for distro-  
    cp -R oozie-4.2.0/distro/target/oozie-4.2.0-distro/oozie-4.2.0/ Oozie

6. Go to new folder "oozie" and create folder libext  
	  mkdir libext

7. Copy libraries from Hadoop 2.7.0 from folder hadoop/share/common,hadoop/share/hdfs and hadoop/share/mapreduce    

8. paste "ext-2.2.zip" in libext folder.

9. Run-      
    ./bin/oozie-setup.sh prepare-war  
  (If any error shows here try to keep a single copy of slf4j and remove all conflicting jar files).

10. Configure hadoop by appending following lines in core-site.xml file-

        <property>
        <name>hadoop.proxyuser.amandeep.hosts</name>
        <value>localhost</value>
        </property>
        <property>
        <name>hadoop.proxyuser.amandeep.groups</name>
        <value>amandeep</value>
        </property>
