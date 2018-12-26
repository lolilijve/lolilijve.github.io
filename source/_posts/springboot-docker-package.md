---
title: springboot项目docker打包
comments: true
date: 2018-08-07 08:52:59
categories: docker
tags: [springboot,docker]
---

### 前置条件：

- ide：Intellij IDEA
    > 安装激活可参照[此文](../idea-install-activate/index.html)

### 1.安装idea docker插件，如图所示：

- > ![安装docker integration](./docker-pic1.png)

### 2.安装docker（Windows版）：

- > 点击[获取docker](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    安装过程不累述，按照提示来即可；安装完启动可看到如下：
    ![安装docker后](./docker-pic3.png)

    右键settings，设置：
    ![settings](./docker-pic4.png)
    内存不足可设置：
    ![settings](./docker-pic5.png)

### 3.idea内docker打包：

- 建立文件Dockerfile
    ```file
    FROM java:8
    EXPOSE 8080

    VOLUME /tmp
    ADD yourProjectName.jar /app.jar
    RUN bash -c 'touch /app.jar'
    ENTRYPOINT ["java","-jar","/app.jar"]
    ```

- 在pom.xml添加plugin
    ```xml
    <build>
        <plugins>
            <plugin>
                <groupId>com.spotify</groupId>
                <artifactId>docker-maven-plugin</artifactId>
                <version>1.1.1</version>
                <configuration>
                    <!-- 路径为：私有仓库地址/你想要的镜像路径 -->
                    <imageName>lolilijve/spider-docker</imageName>
                    <!-- 指定 Dockerfile 路径-->
                    <dockerDirectory>${project.basedir}</dockerDirectory>
                    <!-- 这里是复制 jar 包到 docker 容器指定目录配置，也可以写到 Docokerfile 中 -->
                    <resources>
                        <resource>
                            <targetPath>/</targetPath>
                            <directory>${project.build.directory}</directory>
                            <include>${project.build.finalName}.jar</include>
                        </resource>
                    </resources>
                </configuration>
                <!-- 运行命令 mvn clean package docker:build 打包并生成docker镜像 -->
            </plugin>
        </plugins>
    </build>
    ```

- 设置maven命令：
    > ![maven](./docker-pic2.png)
- 右键执行，结果如下：
    > ![result](./docker-pic6.png)

### 4.push镜像到DockerHub上

- 设置maven的全局settings.xml文件：
    ```xml
    <servers>
        <server>
            <id>docker-registry</id>
            <username>你的DockerHub用户名</username>
            <password>你的DockerHub密码</password>
            <configuration>
                <email>你的DockerHub邮箱</email>
            </configuration>
        </server>
    </servers>
    ```
- 在DockerHub上创建仓库：
    [点击前往](https://cloud.docker.com/)

- pom.xml修改如下：
    ```xml
    <build>
        <plugins>
            <plugin>
                <groupId>com.spotify</groupId>
                <artifactId>docker-maven-plugin</artifactId>
                <version>1.1.1</version>
                <configuration>
                    <!-- 路径为：私有仓库地址/你想要的镜像路径 -->
                    <imageName>lolilijve/spider-docker</imageName>
                    <!-- 指定 Dockerfile 路径-->
                    <dockerDirectory>${project.basedir}</dockerDirectory>
                    <!-- 这里是复制 jar 包到 docker 容器指定目录配置，也可以写到 Docokerfile 中 -->
                    <resources>
                        <resource>
                            <targetPath>/</targetPath>
                            <directory>${project.build.directory}</directory>
                            <include>${project.build.finalName}.jar</include>
                        </resource>
                    </resources>
                    <!-- 与maven配置文件settings.xml中一致 -->
                    <serverId>docker-registry</serverId>
                </configuration>
                <!-- 运行命令 mvn clean package docker:build 打包并生成docker镜像 -->
            </plugin>
        </plugins>
    </build>
    ```
- 命令配置如下：

    ![build&push](./docker-pic7.png)

    右键执行即可,感觉挺久的。。。

    ![pushOver](./docker-pic8.png)