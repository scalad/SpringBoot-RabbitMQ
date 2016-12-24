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

