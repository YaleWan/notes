---
title: hexo+github+next搭建博客网站
categories:
- skill
---

#  个人博客网站的搭建

## 1. 配置好Node和git的环境

## 2. 安装hexo

``` js
npm i hexo -g
```
+ 安装成功后输入`hexo -v` 检查是否安装成功

+ 新建博客项目文件夹，在该文件夹下输入`hexo init`初始化

+ 接着输入`hexo g`体验hexo

+ `hexo s`开启服务器，正式体验Hexo

![1562503394884](C:\Users\shinelon\AppData\Roaming\Typora\typora-user-images\1562503394884.png)

访问localhost:4000出现上图所示代表成功了，如果页面一直无法跳转，那么可能端口被占用了。

+ 输入`hexo server -p 端口号`来改变端口号

## 3. 将hexo与github联系起来

+ 首先在github上新建一个仓库

  项目名称必须要遵守的格式：账号名.github.io，不然会存在问题 

  ![1562504244976](C:\Users\shinelon\AppData\Roaming\Typora\typora-user-images\1562504244976.png)

+ 将github和hexo关联起来，如果是第一次使用Git的话，需要设置一下Git的username和email

  ```js
  git config --global user.name '用户名'
  ```

  ``` js
  git config --global user.email '邮箱地址'
  ```

+ 给GitHub添加ssh密钥

  ``` js
  cd ~/.ssh
  ```

  进入.ssh文件夹，一般在user目录下

  ``` js
  ssh -keygen -t rsa-C '你的邮箱'
  ```

  然后将id_rsa.pub下面的密钥复制到github中的ssh密钥里。

  头像——setting——SSH and GPG keys

+ 配置hexo目录下的_config.yml文件，修改deploy值(在末尾)

  ![1562508205630](C:\Users\shinelon\AppData\Roaming\Typora\typora-user-images\1562508205630.png)

  repository值是GitHub项目里面的

  ![1562508301228](C:\Users\shinelon\AppData\Roaming\Typora\typora-user-images\1562508301228.png)

## 4. 发表一篇文章

+ 新建一篇博客文章

  在hexo文件目录下打开cmd，输入`hexo new post '文章名'`

  或者直接将写好的md文章放到hexo目录下的source中的_posts下面

+ 在部署之前，安装一个扩展`npm i hexo-deployer-git --save`

+ 最终通过`hexo d -g`实现部署。

+ 部署成功后访问地址:`http://GitHub的访问地址`

  github的访问地址在仓库中的setting下可以看到

  ![1562509477847](C:\Users\shinelon\AppData\Roaming\Typora\typora-user-images\1562509477847.png)



  ![1562509537440](C:\Users\shinelon\AppData\Roaming\Typora\typora-user-images\1562509537440.png)
  上图所示的标记圈出来就是你网站的地址，如果需要关联域名的话，在下方填写你的域名即可（前提是你域名已经解析成功），然后通过域名访问就行了。注意：如果你是通过域名的方式来访问网站的话，需要在hexo目录下建立一个CNAME的文件，写上你的域名地址，不然的话，你每次通过`hexo d -g`提交新博客，你又要重新在GitHub中的setting下配置一下域名。

## 5. 添加next主题

当然，hexo自带的主题并不是很好看，本文以next主题为例来修改hexo的默认主题

[next的官方文档]([http://theme-next.iissnan.com](http://theme-next.iissnan.com/))

+ 在hexo站点目录下打开cmd窗口

  ``` js
  git clone https://github.com/iissnan/hexo-theme-next themes/next
  ```

+ 下载完成后打开站点配置文件`_config.yml`将theme修改成next即可

  ![1562510548819](C:\Users\shinelon\AppData\Roaming\Typora\typora-user-images\1562510548819.png)