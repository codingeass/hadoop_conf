# hadoop_conf

This repository contains configuration for setup of tools :  

  a) Hadoop  
  b) Hive  
  c) Oozie  
  d) Spark  
  e) Pig  
  f) Hue  
  g) Livy Spark  

## About these tools :

### Apache Hadoop

Hadoop is an open-source software framework for storing data and running applications on clusters of commodity hardware. 
The Apache Hadoop software library is a framework that allows for the distributed processing of large data sets across clusters of computers using simple programming models. It is designed to scale up from single servers to thousands of machines, each offering local computation and storage. Rather than rely on hardware to deliver high-availability, the library itself is designed to detect and handle failures at the application layer, so delivering a highly-available service on top of a cluster of computers, each of which may be prone to failures. 

 The project includes these modules:

 1. **Hadoop Common:** The common utilities that support the other Hadoop modules.
    
 2. **Hadoop Distributed File System (HDFS™):** A distributed file system that provides high-throughput access to application data.
    
 3. **Hadoop YARN:** A framework for job scheduling and cluster resource management.
    
 4. **Hadoop MapReduce:** A YARN-based system for parallel processing of large data sets.

Learn more about hadoop from https://github.com/youngwookim/awesome-hadoop    

(source : http://hadoop.apache.org/)

### Apache Hive

The Apache Hive ™ data warehouse software facilitates querying and managing large datasets residing in distributed storage. Hive provides a mechanism to project structure onto this data and query the data using a SQL-like language called HiveQL. At the same time this language also allows traditional map/reduce programmers to plug in their custom mappers and reducers when it is inconvenient or inefficient to express this logic in HiveQL.  

Components of Hive include HCatalog and WebHCat.
    **HCatalog** is a component of Hive. It is a table and storage management layer for Hadoop that enables users with different data processing tools — including Pig and MapReduce — to more easily read and write data on the grid.  
    **WebHCat** provides a service that you can use to run Hadoop MapReduce (or YARN), Pig, Hive jobs or perform Hive metadata operations using an HTTP (REST style) interface.  
    
Hive services :

  1. **cli** : The command-line interface to Hive. This is default service
  2. **hiveserver2** : HiveServer2 is an optional service that allows a remote client to submit requests to Hive, using a variety of programming languages, and retrieve results. HiveServer2 is built on Apache Thrift (http://thrift.apache.org/), therefore it is sometimes called the Thrift server.   
  3. **beeline** :  Beeline provide equal functionality, yet is implemented differently from Hive CLI. It works in embedded mode.  
  4. **hwi** : The Hive Web Interface, abbreviated as HWI, is a simple graphical user interface (GUI). ( https://cwiki.apache.org/confluence/display/Hive/HiveWebInterface )  
  5. **jar** : A convient way to run Java applications that includes both Hive and Hadoop classes on the classpath.  
  6. **metastore** : All the metadata for Hive tables and partitions are accessed through the Hive Metastore. Metadata is persisted using JPOX ORM solution (Data Nucleus) so any database that is supported by it can be used by Hive. Most of the commercial relational databases and many open source databases are supported.   
  List of supported databases :

|Database Minimum |Supported Version| Name for parameter Values | 
|:----:|:----:|:----:|
|MySQL|	5.6.17|	mysql|
|Postgres|	9.1.13|	postgres|
|Oracle|	11g	|oracle|
|MS SQL Server|	2008 R2|	mssql|

  

Learn more about hive from https://cwiki.apache.org/confluence/display/Hive/Home  

(source : hive.apache.org)
