---
title: idea的安装和激活
comments: true
date: 2018-08-01 22:54:56
categories: ide
tags: [idea,install]
---
1. 去官网下载并安装 idea，[点击此处跳转](https://www.jetbrains.com/idea/download/)

2. 下载JetbrainsCrack-2.10，放入IntelliJ_IDEA的bin目录（其实放哪都可以）
   - 链接：https://pan.baidu.com/s/1arlX88Shc4LLbtpsFcNnWg 密码：i0kf

3. 修改idea64.exe.vmoptions文件（位于bin目录下，如果您使用的是idea.exe请修改idea.exe.vmoptions，反正两个都改肯定没错），在文件最后添加一行：

   ``` code
    -javaagent:./JetbrainsCrack-2.10-release-enc.jar
    ```

4. 重启idea，help->register->activation code，输入以下代码：

    ``` json
    {"licenseId":"4335",
    "licenseeName":"YuJia",
    "assigneeName":"",
    "assigneeEmail":"",
    "licenseRestriction":"Unlimited license till end of the century.",
    "checkConcurrentUse":false,
    "products":[
    {"code":"II","paidUpTo":"2099-12-31"},
    {"code":"DM","paidUpTo":"2099-12-31"},
    {"code":"AC","paidUpTo":"2099-12-31"},
    {"code":"RS0","paidUpTo":"2099-12-31"},
    {"code":"WS","paidUpTo":"2099-12-31"},
    {"code":"DPN","paidUpTo":"2099-12-31"},
    {"code":"RC","paidUpTo":"2099-12-31"},
    {"code":"PS","paidUpTo":"2099-12-31"},
    {"code":"DC","paidUpTo":"2099-12-31"},
    {"code":"RM","paidUpTo":"2099-12-31"},
    {"code":"CL","paidUpTo":"2099-12-31"},
    {"code":"PC","paidUpTo":"2099-12-31"},
    {"code":"DB","paidUpTo":"2099-12-31"},
    {"code":"GO","paidUpTo":"2099-12-31"},
    {"code":"RD","paidUpTo":"2099-12-31"}
    ],
    "hash":"2911276/0",
    "gracePeriodDays":7,
    "autoProlongated":false}
    ```

上述中licenseeName为显示的授权对象，可随意修改（基本上都可以随意修改，看着办吧）。
激活后显示如下：
![pic](./1533135664.png)

然后，能用到2099年呢，反正我肯定活不了这么久，否则肯定就是程序员当得不称职。

#### 最后，还是要说一句：此破解方法仅供学习使用，如果资金条件允许，请*支持正版*。（反正我的资金条件从来没允许过）