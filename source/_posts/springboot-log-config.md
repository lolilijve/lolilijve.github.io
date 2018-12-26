---
# 标题，（评论对应的唯一标识，请勿重复！请勿修改！）
title: springboot + slf4j + logback 配置
# 分类
categories: log
# 标签
tags: [springboot,slf4j,logback,配置文件]
# 是否开启评论
comments: true
---

spring-boot-starter包已经依赖了logback和slf4j,所以此处不需要再添加其他依赖。如下图：
![img1](./9QBZR9DVK8VALSML.png)

idea打开jar包依赖关系图步骤如下图所示：
![img2](./ACU2RL92D2839IZMY.png)

配置文件优先级：logback-spring.xml > logback-test.xml > logback.xml
## logback-spring.xml
```
<?xml version="1.0" encoding="UTF-8"?>
<configuration>

    <property name="LOG_HOME" value="/logs/spider"/>
    <property name="myAppName" value="spider"/>

    <!--定义日志文件的存储地址 勿在 LogBack 的配置中使用相对路径-->
    <!-- 控制台输出 -->
    <appender name="STDOUT" class="ch.qos.logback.core.ConsoleAppender">
        <encoder class="ch.qos.logback.classic.encoder.PatternLayoutEncoder">
            <!--格式化输出：%d表示日期，%thread表示线程名，%-5level：级别从左显示5个字符宽度%msg：日志消息，%n是换行符-->
            <pattern>%d{yyyy-MM-dd HH:mm:ss.SSS} [%thread] %-5level %logger{50} - %msg%n</pattern>
        </encoder>
    </appender>
    <!-- 按照每天生成日志文件 -->
    <appender name="FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <filter class="ch.qos.logback.classic.filter.ThresholdFilter">
            <level>WARN</level>
        </filter>
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
            <!--日志文件输出的文件名-->
            <FileNamePattern>${LOG_HOME}/log_%d{yyyy-MM-dd}.log</FileNamePattern>
            <!--日志文件保留天数-->
            <MaxHistory>30</MaxHistory>
        </rollingPolicy>
        <encoder class="ch.qos.logback.classic.encoder.PatternLayoutEncoder">
            <charset>UTF-8</charset>
            <!--格式化输出：%d表示日期，%thread表示线程名，%-5level：级别从左显示5个字符宽度%msg：日志消息，%n是换行符-->
            <pattern>%d{yyyy-MM-dd HH:mm:ss.SSS} [%thread] %-5level %logger{50} - %msg%n</pattern>
        </encoder>
        <!--日志文件最大的大小-->
        <triggeringPolicy class="ch.qos.logback.core.rolling.SizeBasedTriggeringPolicy">
            <MaxFileSize>10MB</MaxFileSize>
        </triggeringPolicy>
    </appender>

    <!-- 日志输出级别 -->
    <root level="WARN">
        <appender-ref ref="STDOUT"/>
        <appender-ref ref="FILE"/>
    </root>

    <!-- 开发、测试环境 -->
    <springProfile name="dev,test">
        <logger name="com.spider.modules.spider.dao" level="DEBUG"/>
        <logger name="com.spider.modules.business.dao" level="DEBUG"/>

        <logger name="org.springframework.web" level="INFO"/>
        <logger name="org.springboot.sample" level="INFO"/>
        <logger name="com.spider" level="INFO"/>
    </springProfile>

    <!-- 生产环境 -->
    <springProfile name="prod">
        <logger name="org.springframework.web" level="ERROR"/>
        <logger name="org.springboot.sample" level="ERROR"/>
        <logger name="com.spider" level="ERROR"/>
    </springProfile>

</configuration>
```