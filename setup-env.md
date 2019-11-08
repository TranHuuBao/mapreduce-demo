
# Setup enviroment for map-reduce course
This is instruction for setup enviroment and development tools for mapreduce tutorial
- JAVA 8
- Maven
- IntelliJ IDE
## JAVA 8
Install JAVA 8 if you haven't: 
Checking version by command:
```java -version```
### Windows: 
- Download JDK 8 : 
	We will download [jdk-8u231-windows-x64.exe](https://download.oracle.com/otn/java/jdk/8u231-b11/5b13a193868b4bf28bcb45c792fce896/jdk-8u231-windows-x64.exe)
	you need to sign in oracle account. If you don't have, please create a new account and download it.
-  Install JDK:
	Open Download folder: run file jdk-8u231-windows-x64.exe
	Choose folder for install JDK and JRE ( please remember it for next step )
- Add JAVA_HOME system variable
	- Press Windows key, type `adva` and clicks on the `View advanced system settings`
	- In System Properties dialog, select `Advanced` tab and clicks on the `Environment Variables...` button.
	- In “Environment variables” dialog, `System variables`, Clicks on the `New...` button and add a `JAVA_HOME` variable and point it to ` path-to-JDK `
- Add %JAVA_HOME%\bin To PATH
	- In system variables, find `PATH`, clicks on the `Edit...` button. In “Edit environment variable” dialog, clicks on the `New` button and add this `%JAVA_HOME%\bin
- Verification
	``` java -version ```
-  [Reference](https://o7planning.org/vi/10377/huong-dan-cai-dat-va-cau-hinh-java)
	
### Mac OS: following command
	> brew cask install java

	> brew tap caskroom/versions

	> brew cask install java8

###  Ubuntu: following command
	
	> sudo add-apt-repository ppa:webupd8team/java
	
	> sudo apt update; sudo apt install oracle-java8-installer
	
	> javac -version
	
	> sudo apt install oracle-java8-set-default
	
- Check java version
	```java -version ```
	
	- Expect: java version 1.8.0_xxx
	``` 
	java version "1.8.0_201"
	Java(TM) SE Runtime Environment (build 1.8.0_201-b09)
	Java HotSpot(TM) 64-Bit Server VM (build 25.201-b09, mixed mode) 
	```
## Install Maven (mvn)
- In this course you need to use maven for pull dependencies
- To verify the Maven installation, in terminal, issue the command `mvn -version`
- Step for install it:
### Windows
- Visit [Maven official website](http://maven.apache.org/download.cgi), download the Maven zip file, for example : `apache-maven-3.6.2-bin.zip`
- Unzip it to a folder. In this article, we are using `c:\opt\apache-maven-3.6.2
- Add MAVEN_HOME system variable
	- Press Windows key, type `adva` and clicks on the `View advanced system settings`
	- In System Properties dialog, select `Advanced` tab and clicks on the `Environment Variables...` button.
	- In “Environment variables” dialog, `System variables`, Clicks on the `New...` button and add a `MAVEN_HOME` variable and point it to `c:\opt\apache-maven-3.6.2
- Add %MAVEN_HOME%\bin To PATH
	- In system variables, find `PATH`, clicks on the `Edit...` button. In “Edit environment variable” dialog, clicks on the `New` button and add this `%MAVEN_HOME%\bin`
- Verification
	``` mvn -version ``` 
- Reference [link](https://www.mkyong.com/maven/how-to-install-maven-in-windows/)
### Mac OS
- Run command:
```
brew install maven
```
If you got a 404 error, try doing a `brew update` just before
- Verification
	``` mvn -version ``` 
### Ubuntu
- Run command:
```bash
sudo apt install maven
```
- If you have any problem please install follow [link](https://linuxize.com/post/how-to-install-apache-maven-on-ubuntu-18-04/) to fix it
- Verification
	``` mvn -version ``` 
## Install Intellij IDE
We will develop in IntelliJ IDE but if you want can use Eclipse (not recommend). 
### Windows
- Download exe file
[Download the installer](https://www.jetbrains.com/idea/download/)  .exe.
- Install  : Run the installer and follow the wizard steps.

### Mac OS
- Download dmg file
[Download the disk image](https://www.jetbrains.com/idea/download/)  .dmg
- Mount the image and drag the IntelliJ IDEA app to the Applications folder.
### Ubuntu
- Install IntelliJ IDEA from the Software Center
- Open Ubuntu Software 
- Type IDEA Community and install 

### Install Maven Plugin 
- Open IntelliJ and click button Configure at left bottom.
- Click Plugin and type maven in search bar 
- Install *Maven Integration* 
- Restart IDE

## Create Example project
- Open IntelliJ IDE
- Click: File -> New -> Project -> Maven 
- Type GroupId and ArtifactId 
- Type Project name (if you want to change)
- Create a package in src.main.java: in this article, we are using *demo*
- Create new java class in src.main.java.demo: we are using *HelloWorld*
- Insert code to class HellloWorld
```
public static void main(String[] args) {
	System.out.println("Hello World!");
}
```
- Press Ctrl + Shirft + F10 for running class
- Output: 
```
Hello World!
```

- edit pom.xml and insert :
```xml
<dependencies>
	 <dependency> <groupId>org.apache.hadoop</groupId>
		 <artifactId>hadoop-core</artifactId>
		 <version>1.2.1</version>
	 </dependency>
 </dependencies>
```
- Open terminal and run command:
``` cd $path-to-project && mvn install ```
- If it is not work please check your proxy. Please add it for mvn
	- Please add it for maven to file $MAVEN_HOME/conf/setting.xml
```xml
  <proxies>
    <proxy>
      <id>optional</id>
      <active>true</active>
      <protocol>http</protocol>
      <host>proxy.host</host>
      <port>80</port>
    </proxy>
  </proxies>
```
- If it work ok. Congratulations!!
You set up successful enviroment for map-reduce course!
