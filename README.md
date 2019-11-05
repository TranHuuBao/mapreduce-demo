
# Map reduce tutorial 
## Objectives of this tutorial
- Understand about how to excutable of hadoop map-reduce.
- Know about advantage and disadvantage of map-reduce.

## Problem
- Count number post per year by post type
- Input:

| id |date_time  |post_id|type_post|is_badge|user_id|
|--|--|--|--|--|--
| 3 | 2008-09-15T08:55:03.923 |82946|Teacher|false|3718
|3|2008-09-15T08:55:03.957|82947|Teacher|false|994 


## Pull source code mapreduce
We was develop a simple project mapreduce for demo. You need to clone it and build for your exercise.
```> git clone https://github.com/TranHuuBao/mapreduce-demo.git ```
> ```pom.xml ```: It contains dependencies for this project
> ``` Demo.java```:  Source code mapreduce 
	- ```Map class```: operate map phase
	- ```Reduce class```: operate reduce phase
## Export excutable jar file
### Open project course with Intellij IDE 
On toolbar click ```File -> Open -> path-to-project```

> Wait some minutes for mvn pull external libraries 

### Export jar file 
Open terminal and run below command 
```> cd $path-to-project && mvn install && mvn package```

> ```mvn install```  will download dependencies was configured in  pom.xml 

> ``` mvn package ``` will export jar file for project
## Copy excutable jar file to server
- After export jar file we need to copy it to server for run example
- In ubunu or Mac OS you  can use *scp* with command
	``` >	scp $path-to-project/target/course-1.0-SNAPSHOT.jar user@ip-server: $path-folder-on-server ```
- In windows you can follow [link](https://success.tanaza.com/s/article/How-to-use-SCP-command-on-Windows)
## Run application
- connect to server
	- run command:  
	```> ssh user@ip-server```
- Check input data:
	``` > hdfs dfs -cat /data/input/data-badges.csv ```
- Submit job by command in server
```> hadoop jar $path-to-project/target/course-1.0-SNAPSHOT.jar demo.Demo /data/input/data-badges.csv /data/output/ ```

	- hadoop jar will execute jar file course-1.0-SNAPSHOT.jar 
	- demo.Demo is class we want to run 
	- /data/input/data-badges.csv is input file
	- /data/output is output folder job must to write result

## Result
- Check result : 
	```
	> hadoop fs -cat /data/output/* 
	> hdfs dfs -cat /data/output/*
	 ```
- Expect result:
```
	Autobiographer	2008	6273
	Autobiographer	2009	12701
	Autobiographer	2010	14480 
```
## Kill application
- When you running a application on hadoop but you want to stop it. You can use command:
	 ``` > mapred job -kill $application-id ```
# Exercise 
