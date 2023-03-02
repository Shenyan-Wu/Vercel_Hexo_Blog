---
title: Gitbook 安装及入门
date: 2023-02-25 17:35:16
tags: 
	- "Gitbook"
	- "教程"
top_img: https://s2.loli.net/2023/02/25/tjqaNrogYkPxcJI.png
cover: https://s2.loli.net/2023/02/25/tjqaNrogYkPxcJI.png
---
# Gitbook 安装及入门

## 环境配置

首先，需要保证你拥有 Gitbook 所需要的安装环境 [Node.js](https://nodejs.org/en/) ，奇数版本一般不稳定且不会长期维护，建议选择 Node.js 的偶数版本，个人试验后，发现在较低的 Node.js 版本中，Gitbook安装中不会出现错误，本文选择 10 版本来安装。

### Node.js 安装

首先需要下载  [Node.js](https://nodejs.org/en/) ，进入页面后你会看到下图所示，点击 [Other Downloads](https://nodejs.org/en/download/)

![Nodejs](https://s2.loli.net/2023/02/25/sEwaldkZcKo1e7T.png)

接下来可以通过下载包管理安装或者在先前发行版中选择对应版本，如果你更喜欢使用最新的Node及npm版本，那么建议你可以使用包管理器安装喜欢的版本，由于我使用 Windows 版本，我选择了 [NVS](https://github.com/jasongin/nvs/releases) 作为我的包管理器    [nvs介绍链接](https://nodejs.org/en/download/package-manager/#nvs)

![nodejsdownload](https://s2.loli.net/2023/02/25/BSKTLE9e1kACzVW.png)

安装完成 nvs 后，可以指定选择你需要在当前环境中添加或使用的 Node 版本，如下图

![nvs](https://s2.loli.net/2023/02/25/mtbP1IuxowFWrfE.png)

> 可以看出我添加了两个版本的Node（nvs ls），并选择当前使用 10.24.1 版本，help有许多可用的帮助供你查看，或者去 [nvs介绍链接](https://nodejs.org/en/download/package-manager/#nvs) 来查看用法

### Gitbook安装 

在使用 `node -v` 出现正确的版本号后，此时便可以开始正确安装 Gitbook，命令如下

```shell
npm install -g gitbook-cli
```

之后输出版本进行安装（可能需要一些时间，耐心等待）

```shell
gitbook -V
```

![gitbookversion](https://s2.loli.net/2023/02/25/P4WVrsDzQZbBdGR.png)

## 入门

### Gitbook文档目录结构

```plaintext
GitBook 基本的目录结构如下所示
|- book.json		//配置文件，配置相关信息，插件等
|- README.md		//说明文件，即打开Gitbook的首界面，主要用来写文章摘要等
|- SUMMARY.md		//关联Gitbook的左侧目录
|- chapter01/		//章节1文件夹(chapter-1是文件夹名称，可以自定义)
	|- README.md	    //章节1的摘要简介等
 	|- 文档1.md			//章节下面的小节1（可以自定义）
    |- 文档2.md			//章节下面的小节2（可以自定义）
|- chapter02/		//章节2文件夹(chapter-2是文件夹名称，可以自定义)
	|- README.md	    //章节2的摘要简介等
 	|- 文档1.md			//章节下面的小节1（可以自定义）
    |- 文档2.md			//章节下面的小节2（可以自定义）
```

### Gitbook初始化

在你需要存放Gitbook的一个空文件夹下，使用命令在该文件夹下进行初始化

```javascript
gitbook init
```

会自动在目录中生成两个文件，一个是主要摘要文件(README.md)，一个是目录文件(SUMMARY.md)

![image-20230225142328858](https://s2.loli.net/2023/02/25/FBCru8TL1bzM3pw.png)

此时你可以继续输入以下命令，预览一个初始化后的Book页面

```shell
gitbook build && gitbook serve
```

![initBook](https://s2.loli.net/2023/02/25/5jn7XudcLqsRJ3r.png)

打开浏览器输入 localhost:4000 预览页面

![BookPage](https://s2.loli.net/2023/02/25/ypfh3ob4BCmP7gG.png)

> 运行后目录里会出现一个 `_book` 的文件夹，里面放置的文件就是预览的静态页面

### Gitbook目录

如上图左侧，为导航栏目录，其中的配置需要在目录文件(SUMMARY.md)中进行。配置目录的格式与 Markdown语法 相似，如下：

```text
[目录或章节名称](目录或章节文件相对Book根目录所在的位置)
```

结构类似如下

![summary](https://s2.loli.net/2023/02/25/7bFINWXDupmtrHK.png)

> 文件后面添加 # + name 可以实现区域导航

如此后运行 `gitbook build && gitbook serve`，预览界面

![Preview1](https://s2.loli.net/2023/02/25/yXOgruUJlfCnhTF.gif)

### Gitbook配置文件

在文件夹根目录下新建一个 book.json 文件，作为配置文件

主要内容如下：

```json
{
    "title": "GitBook Learning",
    "description": "My personal learning notes",
    "Author": "Shenyan Wu",
    "language": "zh-hans",
    "root": "./source",
    "plugins": [
        "hide-element",
        "back-to-top-button",
        "chapter-fold",
        "code"
    ],
    "pluginsConfig": {
        "hide-element": {
            "elements": [".gitbook-link"]
        }
    }
}
```

> 此处主要解释一下 “root”，可以改变编译时文章文件的目录，如我的 “root” 修改为 "./source"，即为文件夹下的 source 文件夹，将配置文件与文章文件隔离开来，具体内容如下图所示

根目录如下

![rootd](https://s2.loli.net/2023/02/25/AGZPxLRqVUuivcO.png)

source 目录如下

![sourced](https://s2.loli.net/2023/02/25/TSBtMIfbLrJDke9.png)

### Gitbook配置插件

在 book.json 文件中的 plugin 中的内容即为插件名称，具体插件暂不列出，有兴趣可查询相关教程

```json
"plugins": [
        "hide-element",
        "back-to-top-button",
        "chapter-fold",
        "code"
    ],
"pluginsConfig": {
        "hide-element": {
            "elements": [".gitbook-link"]
        }
    }
```

如上，将相关插件的名称和配置写好后，在生成预览文件前，运行以下命令

```shell
gitbook install
```

或这直接这样

```shell
gitbook install && gitbook build && gitbook serve
```

