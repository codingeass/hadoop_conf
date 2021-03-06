Analysis on Twitter Data-
=========================

1. First Pull twitter data using Flume

    a) Create twitter app by going to URL http://apps.twitter.com/.  
    b) Replace consumer key, consumer secret, access token and access token secret in flume.conf.  
    c) Change keyword and other parameters in flume.conf according to your need.   
       Check this page for details about various parameters :-   
       https://cwiki.apache.org/confluence/display/FLUME/Getting+Started  
    d) In flume directory run following command :-  
        
          bin/flume-ng agent --conf conf --conf-file flume.conf --name TwitterAgent -Dflume.root.logger=INFO,console
2. Start Hue and hiveserver2 by following commands (If want to use hive editor, otherwise just type `hive --service cli` to access command-line interface):

    a) `cd hue` and type `build/env/bin/hue runserver`
    b) To start hive type :- `hive --service hiveserver2`
      ( By starting hiveserver2, Hive runs as a server exposing a Thrift service, enabling access from a range of clients written in different languages. That's how the hue is able to access hive to run command from hive editor.)  

3. In hive editor or hive cli type :-

        ADD JAR /<jar file location>/hive-serdes-1.0-SNAPSHOT.jar;

  It adds hive's SerDes or serializer/deserializer, which indicates how to process data from/into tables.

4. Run following command to create table `tweets` :       

        CREATE EXTERNAL TABLE tweets (
          id BIGINT,
          created_at STRING,
          source STRING,
          favorited BOOLEAN,
          retweeted_status STRUCT<
            text:STRING,
            `user`:STRUCT<screen_name:STRING,name:STRING>,
            retweet_count:INT>,
          entities STRUCT<
            urls:ARRAY<STRUCT<expanded_url:STRING>>,
            user_mentions:ARRAY<STRUCT<screen_name:STRING,name:STRING>>,
            hashtags:ARRAY<STRUCT<text:STRING>>>,
          text STRING,
          `user` STRUCT<
            screen_name:STRING,
            name:STRING,
            friends_count:INT,
            followers_count:INT,
            statuses_count:INT,
            verified:BOOLEAN,
            utc_offset:INT,
            time_zone:STRING>,
          in_reply_to_screen_name STRING
        )  
        ROW FORMAT SERDE 'com.cloudera.hive.serde.JSONSerDe'
        LOCATION '/user/flume/tweets';
    
    Here LOCATION tells where data is stored in HDFS. If want to take data from local path then remove `LOCATION '/user/flume/tweets'` and end the statement. Run this separate command separately:  
    `LOAD DATA INPATH <LOCATION> INTO TABLE <TABLE NAME LIKE HERE twitter>`. 

RUNNING SIMPLE HIVE QUERIES
===========================

Always run this command `ADD JAR /<jar file location>/hive-serdes-1.0-SNAPSHOT.jar;` as it defines how that data is going to serialized and deserialized.

Run this query to get retweets and tweets of various users.

     SELECT
      t.retweeted_screen_name,
      sum(retweets) AS total_retweets,
      count(*) AS tweet_count
    FROM (SELECT
            retweeted_status.`user`.screen_name as retweeted_screen_name,
             retweeted_status.text,
             max(retweeted_status.retweet_count) as retweets
          FROM tweets
          GROUP BY retweeted_status.`user`.screen_name,
                   retweeted_status.text) t
    GROUP BY t.retweeted_screen_name
    ORDER BY total_retweets DESC
    LIMIT 10;

Output looks like this :-

| |	t.retweeted_screen_name	|total_retweets	|tweet_count|
| ------------- |:-------------:|:---------:|:----:|
|0|	mask303|	1716|	1|
|1|	tableau|	559	|1|
|2|	SoftLayer|	125	|1|
|3|	CloudExpo|	87	|10|
|4|	Mackey_Trib|	37|	1|
|5|	LUFC	|30	|1|
|6|	DrSanjayPSahoo|	26	|19|
|7|	macworld|	17|	1|
|8|	WHMeanor|	|11	|11|
|9|	hortonworks|	11|	1|

If using hive editor you can visualize this result :-

![TDD](https://raw.githubusercontent.com/codingeass/hadoop_conf/master/Running%20first%20Job/Screenshot.png)

![TDD](https://raw.githubusercontent.com/codingeass/hadoop_conf/master/Running%20first%20Job/Screenshot_1.png)
