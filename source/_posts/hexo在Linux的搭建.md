---
title: hexo blog build
date: 2021-06-25
---
`CentOS7`搭建

## 准备环境

安装`Node.js`

	>`wget https://nodejs.org/dist/latest-v10.x/node-v10.18.1-linux-x64.tar.gz` 

`node-v10.18.1-linux-x64.tar.gz`是二进制可执行版。不需要编译但是需要自己手动的配置环境变量。

将下载好的文件解压到`/`下的`opt`目录下

> `Linxu`中的`opt`目录用来安装附加软件包，是用户级的程序目录，安装到/opt目录下的程序，它所有的数据、库文件等等都是放在同个目录下面。当不需要的时候可以直接删除。

```shell
#1.解压二进制文件
tar -xzvf node-v10.18.1-linux-x64.tar.gz -C /opt/
#2.配置全局环境变量
vim /etc/profile #追加上
export NODE_HOME=解压后的文件目录 #/opt/node-v10.18.1-linux-x64
export PATH=$NODE_HOME/bin:$PATH
source /etc/profile #重新加载，使环境变量生效
#检测环境变量是否生效
node -v #查看nodejs版本
---- #nmp命令  Node Package Manager 
npm -v
#3.安装淘宝的镜像源cnpm  -g是全局安装
npm install -g cnpm --registry=http://registry.npm.taobao.org
#4.使用cnpm安装hexo博客框架
cnpm install -g hexo-cli
#安装完成后可以使用 hexo -v检查版本信息
```

#### `nmp`工具

```markdown
> Isaac Z. Schlueter 使用 Javascript(运行在Node.js)编写 Node Package Manger
# 实现思路
1. 购买一个服务器作为代码的仓库(registry),在里面方所有需要被共享的代码
2. 共享代码的作者可以给通过 nmp publish将代码提交到registry上,并取一个名字。注意大小写
3. 社区的人如果想使用这些代码，就要下载的名字写到package.json里，然后运行npm install下载
4. 下载后的代码出现在node_modules目录下
> 这些可以被使用的代码被叫做[包] （package）,这就是NPM的由来：Node Package(包) Manage(管理器)
```

## 搭建博客本地目录

1. 选择一个空目录用来当作本地文件库

2. 在目录下使用hexo init生成博客 使用本地localhost:4000访问

3. 启动本地博客hexo start|s

   hexo n 命令可以新创建文件在/博客目录/source/_posts/

   > 创建系的文件后要 1.`hexo clean` 2.`hexo g` 3.` hexo s` 生效

## 将博客搭建到Github

1. 安装git插件 cnmp install --save hexo-deployer-git

2. 设置`_config.ym`

   1. ```yml
      #文件的最底部
      deploy:
        type: git
        repo: github仓库的http地址的地址 # https://github.com/用户名/仓库名.get
        branch: master
      ```

3. hexo d(deploy)  部署到github



## 修改Landscape 主题的标签图标

博客路径下 _config.landscape.yml 文件修改 favicon: /images/favicon.ico 准备好的图片要修改成favicon.ico