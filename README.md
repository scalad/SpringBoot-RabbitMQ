# SpringBoot-RabbitMQ 消息队列

这个指南将引导你建立一个RabbitMQ AMQP服务器发布和订阅消息的过程。

###声明
可以使用本人阿里云安装好的RabbitMQ服务器
	
	host:http://120.27.114.229
	username:root
	password:root
	web management: http://120.27.114.229:15672

###构建
你会使用 Spring AMQP的 RabbitTemplate构建应用系统来发布消息并且使用一个MessageListenerAdapter POJO来订阅消息

###需要
* 15分钟
* 一款文本编辑器或者IDE
* [JDK 1.8+](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
* [Gradle2.3+](http://www.gradle.org/downloads) 或者[Maven3.0+](http://maven.apache.org/download.cgi)
* 你也可以从这个项目中导入代码或者可以在导入[Spring Tool Suite(STS)](https://spring.io/guides/gs/sts)(个人非常喜欢的一款eclipse的IDE)中查看
* RabbitMQ服务器

###如何完成
像许多的Spring [Getting Started guides](https://spring.io/guides)项目,你可以从头开始并完成每一步，或者你可以绕过你已经熟悉的一些步骤，无论是哪种步骤，你最终可以完成代码

从头开始的话，请去看[使用Gradle构建](https://spring.io/guides/gs/messaging-rabbitmq/#scratch)

如果要绕过你熟悉的，按照以下构建：

* [下载](https://github.com/spring-guides/gs-messaging-rabbitmq/archive/master.zip)并解压得到源代码或者从[Git](https://spring.io/understanding/Git)：
	>git clone https://github.com/spring-guides/gs-messaging-rabbitmq.git
* 进入`gs-messaging-rabbitmq/initial`目录
* 跳过[创建RabbitMQ消息接收]()

当你完成时，你可以对比在`gs-messaging-rabbitmq/complete.`目录中的结果和你的结果

###使用Gradle构建
第一步你需要建立一个基本的脚本，当你构建APP应用时你可以任何你喜欢的构建系统，但这些代码你必须要使用到[Gradle](http://gradle.org/)和[Maven](https://maven.apache.org/),如果你对这两个不熟悉，你可以参考[Building Java Projects with Gradle](https://spring.io/guides/gs/gradle)和[Building Java Projects with Maven](https://spring.io/guides/gs/maven)

####1.创建目录结构
在你项目的文件夹中创建如下的子目录结构，例如，在*nix系统中使用命令创建`mkdir -p src/main/java/hello on`

	└── src
	    └── main
	        └── java
	            └── hello

####2.创建Gradle配置文件build.gradle
以下来自[初始化Gradle配置文件](https://github.com/silence940109/SpringBoot-RabbitMQ/blob/master/build.gradle)

`build.gradle`

	buildscript {
	    repositories {
	        mavenCentral()
	    }
	    dependencies {
	        classpath("org.springframework.boot:spring-boot-gradle-plugin:1.4.3.RELEASE")
	    }
	}
	
	apply plugin: 'java'
	apply plugin: 'eclipse'
	apply plugin: 'idea'
	apply plugin: 'org.springframework.boot'
	
	jar {
	    baseName = 'gs-messaging-rabbitmq'
	    version =  '0.1.0'
	}
	
	repositories {
	    mavenCentral()
	}
	
	sourceCompatibility = 1.8
	targetCompatibility = 1.8
	
	dependencies {
	    compile("org.springframework.boot:spring-boot-starter-amqp")
	    testCompile("junit:junit")
	}

[Spring Boot gradle plugin](https://github.com/spring-projects/spring-boot/tree/master/spring-boot-tools/spring-boot-gradle-plugin)提供了很多方便的特性：

* 它集成了所有在类路径下的jar包并构建成单独的jar包，可执行的`über-jar`使它可以更加方便的执行和在你的服务中进行传输
* 它为`public static void main()`方法寻找可执行的类作为标志
* 它提供了一个内置的依赖解析器来匹配[Spring Boot Dependencies](https://github.com/spring-projects/spring-boot/blob/master/spring-boot-dependencies/pom.xml)依赖版本号，你可以重写任何你希望的版本，但它默认启动时选择的版本集合