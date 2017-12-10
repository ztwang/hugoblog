---
title: Install Spark on Windows 10
tags: Windows
date: 2016-06-05 21:45:52
---

[Apache Spark](http://spark.apache.org/) nowadays becomes a super star in the cloud computing industry. It's mainly designed to run on clusters but you can still try it on your own device. This post is to explain how to install Spark on a Windows 10 standalone machine like my old, crappy laptop. :P

## Pre-requisite
If you have checked the Apache Spark website, you should have already known that Spark is based on [Scala](http://www.scala-lang.org/), and Scala is based on Java. I assume you know what Java is and how to install java on your machine. If not, please ask Google about it.
It is highly recommended to use Java 8 with Scala and Spark. This is because of the new features like lambda functions are widely used in Spark.
Before you continue, make sure your Java is correctly installed or updated. Check the version in a command prompt: (My version is 1.8.0_91)
``` bash
C:\> java -version
java version "1.8.0_91"
Java(TM) SE Runtime Environment (build 1.8.0_91-b14)
Java HotSpot(TM) 64-Bit Server VM (build 25.91-b14, mixed mode)
C:\>
```

## Install Scala
Scala installers can be download from [here](http://www.scala-lang.org/download/). Just run it and follow the instructions to complete the installation. It should be very easy.

## Install Spark
Up to now (June 5, 2016), Apache Spark's website has not provided a binary file or installer for Windows users. Just download a pre-built version [here](https://spark.apache.org/downloads.html). Feel free to download the source code and build it yourself if you like. Pre-built version for Hadoop 2.6 and later is recommended.
You will get a tgz file after downloading. Just decompress all the files to a directory.

## Download winutils.exe
The current version of Spark needs a tool called winutils.exe to initialize the Hive context. The 64-bit version of winutils.exe can be download [here](https://github.com/steveloughran/winutils/raw/master/hadoop-2.6.0/bin/winutils.exe). Place this file into a folder named "bin", like "C:\hadoop\bin\". Remember to set an new environment variable HADOOP_HOME with the value of the parent directory. (For example, if winutils.exe is in "C:\hadoop\bin\", the variable value must be "C:\hadoop".)
Some other environment variables are also needed:
* SCALA_HOME: The bin folder in your Scala directory
* SPARK_HOME: The bin folder in your Spark directory

## Check permissions
If you run spark-shell in your spark's bin folder right now, you will probably get an error related to "SqlContext" or something. This is because in Windows system, when Spark initiates Hive, it creates a folder "C:\tmp\hive". However, this folder's permission somehow could not be set correctly for Spark to use. We have to change it manually using winutils.exe:
``` bash
C:\> %HADOOP_HOME%\bin\winutils.exe chmod 777 C:\tmp\hive
```
Now you should be able to run spark-shell without any error.

## References
* https://hernandezpaul.wordpress.com/2016/01/24/apache-spark-installation-on-windows-10/
* https://blogs.msdn.microsoft.com/arsen/2016/02/09/resolving-spark-1-6-0-java-lang-nullpointerexception-not-found-value-sqlcontext-error-when-running-spark-shell-on-windows-10-64-bit/