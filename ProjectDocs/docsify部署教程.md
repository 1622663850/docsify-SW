# docsify部署教程

## 自动化脚本

- [Auto.js Pro编写教程](//pro.autojs.org/docs/#/zh-cn/)


## docsify搭建

Docsify使用指南（打造最快捷、最轻量级的个人&团队文档），[docsify搭建教程](//docsify.js.org/#/zh-cn/)。
[机器视觉全栈er](//github.com/sjtumelc/docsify-template)，可进行参考。

### Node.js 安装配置

- [Node.js下载地址](//nodejs.cn/download/)

- [Node.js最新最详细安装教程](//blog.csdn.net/Small_Yogurt/article/details/104968169)

win+r：cmd进入命令提示符窗口，分别输入以下命令查看node和npm的版本能够正常显示版本号，则安装成功：

- node -v：显示安装的nodejs版本

- npm -v：显示安装的npm版本

- [安装指南](//www.cnblogs.com/Can-daydayup/p/15413267.html)

  ![cmd图](/../image/docsify/cmd图.png)

### docsify-cli工具安装

推荐全局安装 `docsify-cli` 工具，可以方便地创建及在本地预览生成的文档。

```node
npm i docsify-cli -g

```

![img](/../image/docsify/1336199-20220108173008392-698928092.png)

### 项目初始化

如果想在项目的 `./docs(文件名可以按自己的想法来)` 目录里写文档，直接通过 `init` 初始化项目。

```node
docsify init ./Docsify-Guide
```

初始化成功后，可以看到 `./docs` 目录下创建的几个文件

- `index.html` 入口文件
- `README.md` 会做为主页内容渲染
- `.nojekyll` 用于阻止 GitHub Pages 忽略掉下划线开头的文件

直接编辑 `docs/README.md` 就能更新文档内容，当然也可以[添加更多页面](https://docsify.js.org/#/zh-cn/more-pages)。

### 本地运行docsify创建的项目

通过运行 `docsify serve 项目名称 `启动一个本地服务器，可以方便地实时预览效果。默认访问地址 [http://localhost:3000](http://localhost:3000/) 。

```node
docsify serve Docsify-Guide
```

![img](/../image/docsify/1336199-20220108174838887-1798605158.png)

## 基础配置文件介绍

其实我们维护一份轻量级的个人&团队文档我们只需要配置以下这几个基本文件就可以了。

| 文件作用               | 文件          |
| ---------------------- | ------------- |
| 基础配置项（入口文件） | index.html    |
| 封面配置文件           | _coverpage.md |
| 侧边栏配置文件         | _sidebar.md   |
| 导航栏配置文件         | _navbar.md    |
| 主页内容渲染文件       | README.md     |
| 浏览器图标             | favicon.ico   |

## 基础配置项（index.html）

下面是一份基础的配置项模板如下(可直接Copy使用)。

```node
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Docsify-Guide</title>
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
    <meta name="description" content="Description">
    <meta name="viewport"
        content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <!-- 设置浏览器图标 -->
    <link rel="icon" href="/favicon.ico" type="image/x-icon" />
    <link rel="shortcut icon" href="/favicon.ico" type="image/x-icon" />
    <!-- 默认主题 -->
    <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/lib/themes/vue.css">
</head>

<body>
    <!-- 定义加载时候的动作 -->
    <div id="app">加载中...</div>
    
    <script>
        window.$docsify = {
            // 项目名称
            name: 'Docsify-Guide',
            // 仓库地址，点击右上角的Github章鱼猫头像会跳转到此地址
            repo: 'https://github.com/YSGStudyHards',
            // 侧边栏支持，默认加载的是项目根目录下的_sidebar.md文件
            loadSidebar: true,
            // 导航栏支持，默认加载的是项目根目录下的_navbar.md文件
            loadNavbar: true,
            // 封面支持，默认加载的是项目根目录下的_coverpage.md文件
            coverpage: true,
            // 最大支持渲染的标题层级
            maxLevel: 5,
            // 自定义侧边栏后默认不会再生成目录，设置生成目录的最大层级（建议配置为2-4）
            subMaxLevel: 2,
            // 小屏设备下合并导航栏到侧边栏
            mergeNavbar: true,
            //在所有的代码块上添加一个简单的Click to copy按钮来允许用户从你的文档中轻易地复制代码


  
            copyCode: {
                buttonText: '点击复制',
                errorText: '错误',
                successText: '复制成功'
            },
            //添加搜索功能
            search: {
                maxAge: 86400000, // 过期时间，单位毫秒，默认一天
                paths: [], // or 'auto'
                placeholder: 'Type to search',
                // 支持本地化
                placeholder: {
                    '/zh-cn/': '搜索',
                    '/': '搜索'
                },
                noData: 'No Results!',
                // 支持本地化
                noData: {
                    '/zh-cn/': '找不到结果',
                    '/': 'No Results'
                },
                // 搜索标题的最大层级, 1 - 6
                depth: 2,
                hideOtherSidebarContent: false, // 是否隐藏其他侧边栏内容
                // 避免搜索索引冲突
                // 同一域下的多个网站之间
                namespace: 'website-1',
                // 使用不同的索引作为路径前缀（namespaces）
                // 注意：仅适用于 paths: 'auto' 模式
                // 初始化索引时，我们从侧边栏查找第一个路径
                // 如果它与列表中的前缀匹配，我们将切换到相应的索引
                pathNamespaces: ['/zh-cn', '/ru-ru', '/ru-ru/v1'],
                // 您可以提供一个正则表达式来匹配前缀。在这种情况下，
                // 匹配到的字符串将被用来识别索引
                pathNamespaces: /^(\/(zh-cn|ru-ru))?(\/(v1|v2))?/
                },
        }
    </script>
    <!-- docsify的js依赖 -->
    <script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
    <!-- emoji表情支持 -->
    <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/emoji.min.js"></script>
    <!-- 图片放大缩小支持 -->
    <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/zoom-image.min.js"></script>
    <!-- 搜索功能支持 -->
    <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.min.js"></script>
    
    <!--在所有的代码块上添加一个简单的Click to copy按钮来允许用户从你的文档中轻易地复制代码--> 
    <script src="//cdn.jsdelivr.net/npm/docsify-copy-code/dist/docsify-copy-code.min.js"></script>
    <!--代码高亮功能支持--> 
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-bash.min.js"></script>
    <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-php.min.js"></script>
    <!--侧边栏折叠功能支持--> 
    <script src="//cdn.jsdelivr.net/npm/docsify-sidebar-collapse/dist/docsify-sidebar-collapse.min.js"></script>

</body>


</html>
```

在（_coverpage.md）中添加

```node
<!-- _coverpage.md -->

# Docsify使用指南 

> 💪Docsify使用指南，使用Typora+Docsify打造最强、最轻量级的个人&团队文档。

 简单、轻便 (压缩后 ~21kB)
- 无需生成 html 文件
- 众多主题


[开始使用 Let Go](/README.md)
```

![img](/../image/docsify/1336199-20220108173404374-1211179135.png)

## 侧边栏配置文件（_sidebar.md）

```node
<!-- index.html -->

<script>
  window.$docsify = {
    loadSidebar: true
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
```

在index.html基础配置文件中设置了二级目录

![img](/../image/docsify/1336199-20220116225008119-1381171314.png)

在（_sidebar.md）中添加

```
<!-- _sidebar.md -->

* Typora+Docsify使用指南
  * [Docsify使用指南](/ProjectDocs/Docsify使用指南.md) <!--注意这里是相对路径-->
  * [Typora+Docsify快速入门](/ProjectDocs/Typora+Docsify快速入门.md)
* Docsify部署
  * [Docsify部署教程](/ProjectDocs/Docsify部署教程.md)
```

![img](/../image/docsify/1336199-20220108173556949-632626027.png)

## 导航栏配置文件（_navbar.md）

```
<!-- index.html -->

<script>
  window.$docsify = {
    loadNavbar: true
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
```

```
<!-- _navbar.md -->

* 链接到我
  * [博客园地址](https://www.cnblogs.com/Can-daydayup/)
  * [Github地址](https://github.com/YSGStudyHards)
  * [知乎地址](https://www.zhihu.com/people/ysgdaydayup)
  * [掘金地址](https://juejin.cn/user/2770425031690333/posts)
  * [Gitee地址](https://gitee.com/ysgdaydayup)


* 友情链接
  * [Docsify](https://docsify.js.org/#/)
  * [博客园](https://www.cnblogs.com/)
```

![img](/../image/docsify/1336199-20220108173647735-8411738.png)

## 相关教程

- [docsify-github地址](https://github.com/docsifyjs/docsify/#showcase)
- [docsify快速开始-官方教程](https://docsify.js.org/#/zh-cn/quickstart)
- [使用开源文档工具docsify，用写博客的姿势写文档](https://www.cnblogs.com/throwable/p/13605289.html)

- [Typora安装教程](http://www.ddooo.com/softdown/220391.htm)

- [YSGStudyHards主页](https://github.com/YSGStudyHards)
- [Typora使用教程](https://docsify.tb1043.com/#/)
