title: Mac os下hexo+github搭建个人博客
comments: true
date: 2016-02-22 14:57:19
categories: Hexo
tags: [Hexo,github]
---

## 前言
爬贴无数,终于搭建起来了,把遇到的问题和如何解决的记录一下,万一你看到了,有帮助到你也是极好的.

## 准备
 [Github](https://github.com/)上创建一个属于你自己的账户,然后创建一个新的仓库,并且命名为*YourSiteName.github.io/com*,此时Gitub会帮助你初始化一个静态网页,准备工作就结束了,尝试访问一下你创建的站点,成功后就可以开始动工了.(我自己的用的是MAC OS 10.10.5的系统,Win系统需要自行安装Git客户端)
 <!-- more -->
 
## 关于Hexo
### 1. hexo介绍

> A fast, simple & powerful blog framework
> 快速，简单而高效的静态博客框架
> 超快速度： Node.js 所带来的超快生成速度，让上百个页面在几秒内瞬间完成渲染。
> 支持 Markdown： Hexo 支持 GitHub Flavored Markdown 的所有功能，甚至可以整合 Octopress的大多数插件。
> 一键部署： 只需一条指令即可部署到 GitHub Pages, Heroku 或其他网站。
> 丰富的插件： Hexo 拥有强大的插件系统，安装插件可以让 Hexo 支持 Jade, CoffeeScript。

### 2. 关于NexT主题
 
![NexT主题](http://7xr4es.com1.z0.glb.clouddn.com/Snip20160222_2.png)

> NexT 主旨在于简洁优雅且易于使用，所以首先要尽量确保 NexT 的简洁易用性。

> NexT is built for easily use with elegant appearance. First things first, always keep things simple.

## 开始
前期铺垫完成,现在开始搭建.

### 1. Hexo + github配置
安装nodejs
	
>hexo安装和搭建依赖[Nodejs](https://nodejs.org/en/)和Git,可以自行下载.
>安装nodejs方法很多,在MAC下可以用homebrew方式安装
	
安装brewhome

```bash
$ ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)”
``` 
	  
安装nodejs
	  
``` bash
$ brew install node
```
	  
或者是在git下安装:
	  	  
```
$ git clone git://github.com/joyent/node.git
$ cd node
$ ./configure
$ make
$ sudo make install
```
	 
安装Hexo
第一种方式,用nodejs自带npm安装
	
```bash
$ npm install -g hexo
$ hexo init
$ npm install
```
	
配置Git
	 
	安装git
	
```
$ sudo brew install git
```
	
配置
	
``` bash
$ cd ~/.ssh  //检查SSH KEY
$ ssh-keygen -t rsa -C "xxxxx@xxx.com" //生成
```
	 
将ssh key添加到Github
	
	
> Account Settings->SSH Public Keys->Add another key将生成的key(id_rsa.pub文件）内容copy到输入框中，save。 	   	

测试连接

```bash
$ ssh git@github.com
```

初始化HEXO框架

```bash
$ hexo init
$ cd <Folder>
$ npm install
```

**PS: 在Hexo3中,hexo-server独立出来了,如要本地调试,需要先安装**
 
 ```bash
$ npm install hexo-server --save
 ```
 
初始化完成后的目录

``` bash
├── _config.yml //网站的 配置 信息，您可以在此配置大部分的参数。
├── package.json
├── scaffolds 	//模版 文件夹。当您新建文章时，Hexo 会根据 scaffold 来建立文件。
├── source 	//资源文件夹是存放用户资源的地方。
|   ├── _drafts
|   └── _posts
└── themes 	//主题 文件夹。Hexo 会根据主题来生成静态页面。
```

### 2. Hexo新建文章
```bash
$ hexo new [layout] "hello world" 
```
**在 /source/_post 里添加 hello-world.md 文件，之后新建的文章都将存放在此目录下。**

### 3. 生成网站
* 生成

```bash
$ hexo generate   //后期可以用hexo g代替
```

**此时会将 /source 的 .md 文件生成到 /public 中，形成网站的静态文件。**

* 服务器部署

```bash
$ hexo server --debug
或者是
$ hexo server -p 3000
根据提示完成即可
```
### 4. 部署完成后的hexo到github

```bash
$ hexo deploy
```

**部署网站之前需要生成静态文件，即可以用 $ hexo generate -d 直接生成并部署。此时需要在 _config.yml 中配置你所要部署的站点**：
  
  
	## Docs: http://hexo.io/docs/deployment.html
	deploy:
  	type: git
  	repo: git@github.com:YourRepository.git
  	branch: master


## Next主题
### 1. 使用

```bash
$ cd your-hexo-site
$ git clone https://github.com/iissnan/hexo-theme-next themes/next
```

### 2. 启用
	需要修改 /root/_config.yml 配置项 theme：
	
```
# Extensions
## Plugins: http://hexo.io/plugins/
## Themes: http://hexo.io/themes/
theme: next
```
	
* 验证是否启用
	
```
$ hexo s --debug
```
	
## 更多
1. Next官网-[Next](http://theme-next.iissnan.com/)
2. 主题设定-[主题设定](http://theme-next.iissnan.com/theme-settings.html)
3. 第三方服务-[服务](http://theme-next.iissnan.com/third-party-services.html)
4. 为NexT主题添加文章阅读统计功能-[阅读统计](http://www.tuicool.com/articles/YB3EJnz)
5. Hexo插件安装友情链接-[插件安装](http://luuman.github.io/2015/12/27/Hexo-plug)
	


