# Map reduce tutorial 
## Objectives of this tutorial
- Understand about how to excutable of hadoop map-reduce.
- Know about advantage and disadvantage of map-reduce.

## Setup enviroment 
- Java: Install JAVA 8 if you haven't
	- Windows: you can install follow this [link](https://java.com/en/download/help/windows_manual_download.xml)
	- Mac OS: you can instal follow this [link](https://docs.oracle.com/javase/8/docs/technotes/guides/install/mac_jdk.html)
	- Ubuntu: follow command
	
	> sudo add-apt-repository ppa:webupd8team/java
	
	> sudo apt update; sudo apt install oracle-java8-installer
	
	> javac -version
	
	> sudo apt install oracle-java8-set-default
	
- Maven: You can install maven follow instruction in [link](https://www.baeldung.com/install-maven-on-windows-linux-mac) for all OS
- Intellij IDE: You can install it follow instruction in [link](https://www.jetbrains.com/help/idea/installation-guide.html) for all OS.
You can use Eclipse but it is not recommend.

## Pull source code mapreduce
> git clone https://github.com/TranHuuBao/mapreduce-demo.git 
- pom.xml: It contains dependencies for this project
- Demo.java:  Source code mapreduce 
	- Map class: operate map phase
	- Reduce class: operate reduce phase
## Export excutable jar file
### Open project course with Intellij IDE 
On toolbar click File -> Open -> path-to-project
Wait some minutes for mvn pull external libraries 

### Export jar file 
Open terminal: 
> cd $path-to-project && mvn install && mvn package

	- mvn install  will download dependencies in pom.xml 
	- mvn package will export jar file for project
## Copy excutable jar file to server
- After export jar file we need to copy it to server for run example
- In ubunu or Mac OS you  can use *scp* with command
	-	scp $path-to-project/target/course-1.0-SNAPSHOT.jar user@ip-server: $path-folder-on-server 
- In windows you can follow [link](https://success.tanaza.com/s/article/How-to-use-SCP-command-on-Windows)
## Run application
- ssh to server
	- run command: ssh user@ip-server
- Submit job by command in server
> hadoop jar $path-to-project/target/course-1.0-SNAPSHOT.jar demo.Demo /data/input/data-badges.csv /data/output/

	- hadoop jar will execute jar file course-1.0-SNAPSHOT.jar 
	- demo.Demo is class we want to run 
	- /data/input/data-badges.csv is input file
	- /data/output is output folder job must to write result

## Result
- Check result : 
	- hadoop fs -cat /data/output/* 
	- hdfs dfs -cat /data/output/*
- Expect result:
```
	Autobiographer	2008	6273
	Autobiographer	2009	12701
	Autobiographer	2010	14480 
```
