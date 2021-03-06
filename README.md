# hadoop_conf

This repository contains configuration for setup of tools :  

  - [Apache Hadoop](#apache-hadoop)
  - [Apache Hive](#apache-hive)  
  - [Oozie](#oozie)  
  - [Apache Spark](#apache-spark)  
  - [Apache Pig](#apache-pig)  
  - [Apache Hue](#apache-hue)  
  - [Livy](#livy-the-rest-spark-server)  

## About these tools :

### Apache Hadoop
<div id="apache_hadoop"></div>
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


### Oozie

Apache Oozie is a Java Web application used to schedule Apache Hadoop jobs. Oozie combines multiple jobs sequentially into one logical unit of work. It is integrated with the Hadoop stack, with YARN as its architectural center, and supports Hadoop jobs for Apache MapReduce, Apache Pig, Apache Hive, and Apache Sqoop. Oozie can also schedule jobs specific to a system, like Java programs or shell scripts.  



Apache Oozie is a tool for Hadoop operations that allows cluster administrators to build complex data transformations out of multiple component tasks. This provides greater control over jobs and also makes it easier to repeat those jobs at predetermined intervals. At its core, Oozie helps administrators derive more value from Hadoop.  

There are two basic types of Oozie jobs:

  1. **Oozie Workflow** jobs are Directed Acyclical Graphs (DAGs), specifying a sequence of actions to execute. The Workflow job has to wait.  
  2. **Oozie Coordinator** jobs are recurrent Oozie Workflow jobs that are triggered by time and data availability.
  Oozie Bundle provides a way to package multiple coordinator and workflow jobs and to manage the lifecycle of those jobs.
  
  **Oozie Bundle** provides a way to package multiple coordinator and workflow jobs and to manage the lifecycle of those jobs.

(source : http://hortonworks.com/hadoop/oozie/)

### Apache Spark

Apache Spark is an open source cluster computing framework originally developed in the AMPLab at University of California, Berkeley but was later donated to the Apache Software Foundation where it remains today. In contrast to Hadoop's two-stage disk-based MapReduce paradigm, Spark's multi-stage in-memory primitives provides performance up to 100 times faster for certain applications.    
Apache Spark is a fast and general-purpose cluster computing system.   
It provides high-level APIs in following languages: 
  1. Java
  2. Scala
  3. Python
  4. R
It also supports a rich set of higher-level tools including Spark SQL for SQL and structured data processing, MLlib for machine learning, GraphX for graph processing, and Spark Streaming.

Spark requires a cluster manager and a distributed storage system.   
  **Cluster management**: Spark supports standalone (native Spark cluster), Hadoop YARN, or Apache Mesos.  
  **Distributed storage**: Spark can interface with a wide variety, including Hadoop Distributed File System (HDFS), Cassandra, OpenStack Swift, Amazon S3, Kudu, or a custom solution can be implemented. Spark also supports a pseudo-distributed local mode, usually used only for development or testing purposes, where distributed storage is not required and the local file system can be used instead; in such a scenario, Spark is run on a single machine with one executor per CPU core.  

Learn more about Apache Spark from http://spark.apache.org/docs/latest/sql-programming-guide.html .


(source : https://en.wikipedia.org/wiki/Apache_Spark)


### Apache Pig

Pig is a high level scripting language that is used with Apache Hadoop. Pig enables data workers to write complex data transformations without knowing Java. Pig’s simple SQL-like scripting language is called Pig Latin, and appeals to developers already familiar with scripting languages and SQL.  

Pig is complete, so you can do all required data manipulations in Apache Hadoop with Pig. Through the User Defined Functions(UDF) facility in Pig, Pig can invoke code in many languages like JRuby, Jython and Java. You can also embed Pig scripts in other languages. The result is that you can use Pig as a component to build larger and more complex applications that tackle real business problems.  

Pig works with data from many sources, including structured and unstructured data, and store the results into the Hadoop Data File System. Pig scripts are translated into a series of MapReduce jobs that are run on the Apache Hadoop cluster.     

Pig was designed for performing a long series of data operations, making it ideal for three categories of Big Data jobs:

1. **Extract-transform-load (ETL)** data pipelines,  
2. **Research** on raw data, and  
3. **Iterative data processing**.  
 


|Characteristic|	Benefit|
|:----:|:-----|
|Extensible|	Pig users can create custom functions to meet their particular processing requirements|
|Easily programmed|	Complex tasks involving interrelated data transformations can be simplified and encoded as data flow sequences. Pig programs accomplish huge tasks, but they are easy to write and maintain.|
|Self-optimizing|	Because the system automatically optimizes execution of Pig jobs, the user can focus on semantics.|

(Resource : http://hortonworks.com/hadoop/pig/)

### Apache Hue

Hue is an open source Web interface for analyzing data with any Apache Hadoop.

It features:

   * SQL Editors for Hive, Impala, MySql, PostGres, Sqlite and Oracle
   * Dynamic search dashboards for Solr
   * Spark Notebooks
   * Browsers for YARN, HDFS, Hive table Metastore, HBase, ZooKeeper
   * Pig Editor, Sqoop2, Oozie workflows Editors and Dashboards
   * Wizards to import data into Hadoop

On top of that, an SDK is available for creating new apps integrated with Hadoop.

**Hue Architecture**  
Hue applications run in a Web browser and require no client installation.  
<br/>
<p align="center">
  <img src="https://raw.githubusercontent.com/codingeass/hadoop_conf/a1b026bbd140f86b9f1efa2faa3a55157aec20db/hue.jpeg"/>
</p>

(source : http://www.cloudera.com/)

### Livy, the REST Spark Server

Livy is an open source REST interface for interacting with Spark from anywhere. It supports executing snippets of code or programs in a Spark context that runs locally or in YARN.

* Interactive Scala, Python and R shells
* Batch submissions in Scala, Java, Python
* Multi users can share the same server (impersonation support)
* Can be used for submitting jobs from anywhere with REST
* Does not require any code change to your programs

<p align="center">
  <img src="https://raw.githubusercontent.com/codingeass/hadoop_conf/master/Livy%20server%20architecture.png"/>
</p>

(source : http://gethue.com/)
