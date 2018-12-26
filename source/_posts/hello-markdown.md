---
# 标题，（评论对应的唯一标识，请勿重复！请勿修改！）
title: hexo创建帖子
# 分类
categories: hexo
# 标签
tags: [hexo,blog,Markdown]
# 是否开启评论
comments: true
---

## **快速上手**

### 创建一个帖子

``` bash
$ hexo new "My New Post"
```

More info: [Writing](https://hexo.io/docs/writing.html)

### 运行服务

``` bash
$ hexo server
```
或 简写
``` bash
$ hexo s
```

More info: [Server](https://hexo.io/docs/server.html)

### 生成静态文件

``` bash
$ hexo generate
```
或 简写
``` bash
$ hexo g
```

More info: [Generating](https://hexo.io/docs/generating.html)

### 部署到远程

``` bash
$ hexo deploy
```
或 简写
``` bash
$ hexo d
```

More info: [Deployment](https://hexo.io/docs/deployment.html)

### 一般部署操作
``` bash
$ hexo clean && hexo g && hexo d
```
<hr>
分割线
<hr>

## **md 语法**
1. ### 标题

- 用 Markdown 书写时，只需要在文本前面加上『# 』即可创建一级标题。同理，创建二级标题、三级标题等只需要增加『# 』个数即可，Markdown 共支持六级标题。如下所示：
    ``` 
    # 一级标题
    ## 二级标题
    ### 三级标题
    #### 四级标题
    ##### 五级标题
    ###### 六级标题
    ```
    效果如下(为了不影响布局，此处用网上图片代替)：
    ![](https://raw.githubusercontent.com/wjw0315/blog_gitalk/master/2018-1-31-markdown_edit/1.png)

2. ### 引用

- Markdown 标记区块引用，只需要在整个段落的第一行最前面加上 『>』即可 ：
    ```
    > 我的引用内容
    ```
    效果如下：
    > 我的引用内容

- 区块引用可以嵌套，只要根据层次加上不同数量的『>』即可：
    ```
    > 这是第一级引用。
    > > 这是第二级引用。
    ```
    效果如下：
    > 这是第一级引用。
    > > 这是第二级引用。

- 引用的区块内也可以使用其他的 Markdown 语法，包括标题、列表、代码区块等：
    ````
    > - 这是一个标题。
    > 1. 这是第一行列表项。
    > 2. 这是第二行列表项。
    > `var f = function(){}`
    ````

    效果如下：
    > - 这是一个标题。
    > 1. 这是第一行列表项。
    > 2. 这是第二行列表项。
    > `var f = function(){}`

3. ### 列表

列表项目标记通常放在最左边，项目标记后面要接一个字符的空格。

- 无序列表：使用星号、加号或是减号作为列表标记:
    ```
    - Red
    - Green
    + Blue
    + yellow
    * black
    * white
    ```
    效果如下：
    - Red
    - Green
    + Blue
    + yellow
    * black
    * white

- 有序列表：使用数字接着一个英文句点
    ```
    1. Red
    2. Green
    3. Blue
    ```
    效果如下：
    1. Red
    2. Green
    3. Blue

- 代办列表: 表示列表是否勾选状态（注意：[ ] 前后都要有空格）
    ```
    - [ ] 不勾选
    - [x] 勾选
    ```
    效果如下：
    - [ ] 不勾选
    - [x] 勾选

4. ### 代码引用

- 需要引用代码时，如果引用的语句只有一段，不分行，可以用 \` 将语句包起来。如果引用的语句为多行，可以将\`\`\`置于这段代码的首行和末行。（调不好了，放张图凑乎一下）
    ![](https://raw.githubusercontent.com/wjw0315/blog_gitalk/master/2018-1-31-markdown_edit/3.png)

5. ### 强调
    在Markdown中，可以使用 * 和  _  来表示斜体和加粗。

- 斜体：
    ```
    *Coding，让开发更简单*
    _Coding，让开发更简单_
    ```
    效果如下：

    *Coding,让开发更简单;*
    _Coding,让开发更简单._
- 加粗：
    ```
    **Coding，让开发更简单**
    __Coding，让开发更简单__
    ```
    效果如下：

    **Coding，让开发更简单**
    __Coding，让开发更简单__

6. ### 链接
    方括号显示说明，圆括号内显示网址， Markdown 会自动把它转成链接，例如：

    [百度一下](https://www.baidu.com)

7. ### 表格
- 在 Markdown 中，可以制作表格，例如：
    ```
    First Header | Second Header | Third Header
    ------------ | ------------- | ------------
    Content Cell | Content Cell  | Content Cell
    Content Cell | Content Cell  | Content Cell
    ```
    效果如下：

First Header | Second Header | Third Header
------------ | ------------- | ------------
Content Cell | Content Cell  | Content Cell
Content Cell | Content Cell  | Content Cell

- 也可以让表格左右对齐或居中，例如：
    ```
    First Header | Second Header | Third Header
    :----------- | :-----------: | -----------:
    Left         | Center        | Right
    Left         | Center        | Right
    ```
    效果如下：
    
First Header | Second Header | Third Header
:----------- | :-----------: | -----------:
Left         | Center        | Right
Left         | Center        | Right

8. ### 图片
    Markdown 使用了类似链接的语法来插入图片, 包含两种形式: 内联 和 引用.

- 内联图片:
    ```
    ![bg](/public/img/bg.png)
    或
    ![sidebar_header](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1529440322654&di=86d45751742055d4ba39c9158164aa84&imgtype=0&src=http%3A%2F%2Fimg3.duitang.com%2Fuploads%2Fitem%2F201508%2F28%2F20150828095653_N4zGY.jpeg "古风")
    ```
    效果如下：
    ![bg](/img/bg.png)
    或
    ![sidebar_header](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1529440322654&di=86d45751742055d4ba39c9158164aa84&imgtype=0&src=http%3A%2F%2Fimg3.duitang.com%2Fuploads%2Fitem%2F201508%2F28%2F20150828095653_N4zGY.jpeg "古风")

    也就是:
    
    一个惊叹号『!』
    接着一个方括号，里面是图片的替代文字，接着一个圆括号，里面是图片的地址，最后还可以用引号包住并加上选择性的『title』文字进行悬停显示。

- 引用图片:
    ```
    [id]: /public/img/bg.png "大风车，吱呀呀地转"
    ![][id]
    ```
    『id』 是图片引用的名称. 图片引用使用链接定义的相同语法
    
    效果如下：

[id]: /img/bg.png "大风车，吱呀呀地转"
![cc][id]

[hexo官方文档](https://hexo.io/zh-cn/docs/index.html)