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

ADD JAR /home/amandeep/Downloads/hive-serdes-1.0-SNAPSHOT.jar;
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
