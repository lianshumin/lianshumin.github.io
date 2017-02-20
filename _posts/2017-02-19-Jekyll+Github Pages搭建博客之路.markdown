---
layout: post
title: Jekyll+Github Pages搭建博客之路
date: 2017-02-19 22:30:00.000000000 +08:00
---

​	之前使用wordPress搭建的博客是架设在Amazon EC2，一年免费期限已到，决定搬家到Github上。搭建前，在HEXO和Jekyll间小纠结了下，最终选择Jekyll。

[^1]: [HEXO](https://hexo.io/)基于Node.js，操作简单，支持Markdown，本地运行远程发布，低负载，高速度，”市场“占有率高。
[^2]: [Jekyll](http://jekyllcn.com/)比较源生，操作稍复杂，支持Markdown，远程编写及发布。灵感一来，随时随地在Github上写博客。Bingo~

开始啦：

1. 创建仓库

   + 登录Github创建仓库

2. 克隆仓库

   + SourceTree 克隆到本地，建议Https，不要SSH。

3. Jekyll本地环境搭建

   [^3]: Jekyll的核心是一个文本的转换引擎，用Markdown、Textile、HTML写文档，再通过layout将文档拼装起来，根据你设置的URL规则来展现，这些都是通过严格的配置文件来定义，最终的产出就是web页面。[GitHub Pages](https://pages.github.com/)为了提供对HTML内容的支持，选择了Jekyll作为模板系统。

   - 选择喜欢的[主题](http://jekyllthemes.org/)。我选择喵神的[vno](https://github.com/onevcat/OneV-s-Den)。下载到SourceTree本地目录里。

   - 安装Ruby（一般Mac自带Ruby版本比较低，请自行升级）

   - 安装Jekyll

     ```
     $ sudo gem install jekyll
     ```

   - 安装bundle

     ```
     $ cd /Users/lianshumin/iOS/Git/Blog
     $ sudo gem install bundle
     $ bundle install
     ```

     > ERROR: While executing gem ... (Gem::Exception) Unable to require openssl, install OpenSSL and rebuild ruby (preferred) or use non-HTTPS sources。
     >
     > 这里OpenSSL出问题：需安装Openssl，找到Ruby安装路径，重安装Ruby，并设置为默认。
     >
     > ```
     > $ rvm pkg install openssl
     > $ ~/.rvm/usr
     > $ rvm install 2.3.0 --with-openssl-dir=/Users/lianshumin/.rvm/usr
     > $ rvm 2.3.0 --default
     > ```

   - 开启Jekyll环境

     ```
     $ bundle exec jekyll serve
     ```

   - 浏览器打开http://127.0.0.1:4000/，本地博客OK。

   - SouceTree上传到GitHub上，浏览器打开https://lianshumin.github.io/，远程博客OK。


4. 绑定个人域名
   + 进入本地博客目录，创建文件CNAME，不带后缀。写入裸域名imlian.com 。

   + 域名解析。之前已经在Namecheap.com上购入了域名，登陆后设置即可。

     ```
     192.30.252.153
     192.30.252.154
     ```

5. 添加Disque评论

   + 注册Disque账号，Setting -> Add disqus to site -> Start Using Engage -> imlian.disqus.com
   + 设置本地目录下`_config.yml`文件的disqus的URL，disqus: imlian。

6. 细节修改

   （to be continued）

7. 发布博客

   （to be continued)

> warning: You are attempting to use the 'pygments' highlighter, which is currently unsupported on GitHub Pages. Your site will use 'rouge' for highlighting instead. To suppress this warning, change the 'highlighter' value to 'rouge' in your '_config.yml' and ensure the 'pygments' key is unset.
>
> 收到Github邮件提醒。很简单，把_config.yml 里把pygments替换为rouge，再更新下就可以了。
>
> ```
> $ cd /Users/lianshumin/iOS/Git/Blog
> $ Bundle updated
> ```


