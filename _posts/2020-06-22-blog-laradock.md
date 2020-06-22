---
layout: post
title: Docker-laradock
categories: GitHub
description: laradock
keywords: docker,集成环境,larddock
topmost: true
---

Laradock是用于Docker的完整PHP开发环境。
它支持各种通用服务，所有这些服务都已预先配置为提供现成的PHP开发环境。

### [首先使用Docker-然后再了解它！](https://www.runoob.com/docker/macos-docker-install.html)
```php 
1.在PHP版本之间轻松切换：7.4、7.3、7.2、7.1、5.6…
2.选择您喜欢的数据库引擎：MySQL，Postgres，MariaDB…
3.运行自己的堆栈：Memcached，HHVM，RabbitMQ…
4.每个软件都在自己的容器上运行：PHP-FPM，NGINX，PHP-CLI…
5.只需对进行简单的编辑，即可轻松自定义任何容器Dockerfile。
6.所有图像均来自官方基础图像。（受信任的基本图像）。
7.预先配置的NGINX可以在根目录中托管任何代码。
8.每个项目可以使用Laradock，或者所有项目可以使用一个Laradock。
9.使用环境变量可轻松在Containers中安装/删除软件。
10.干净且结构良好的Dockerfile（Dockerfile）。
11.最新版本的Docker Compose文件（docker-compose）。
11.一切都可见且可编辑。
12.快速图像生成
```

特征
### docker常用基本命令
* docker pull 获取image
* docker build 创建image
* Docker ps 查看容器里的镜像
* docker images	查看当前的镜像
* docker rmi -f xxx  强制删除某个镜像
* Docker kill xxxx   停止ID 


* 容器导入镜像的命令是 (如果你有打包好的镜像)
 ``` docker load < nginx:latest 导入后 docker tag  id  名字 ```
 

####  有关 Laravel 官网的docker教程

#### 快速上手
* 深入了解 Laradock 之前让我们先见识下如何在 Laradock 中快速安装 Nginx、PHP、Composer、MySQL、Redis 和 Beanstalkd 吧，有了这些开发Laravel必备的工具组件也就差不离了。
 1. 首先将 Laradock 项目代码克隆到本地  
    ```git 
    git clonehttps://github.com/Laradock/laradock.git 

    ```

 2. 进入 laradock 目录将 env-example 重命名为 .env：

    ``` 
    cp env-example .env
    ```
    * 补充-env根据所需安装扩展包
 3. 运行容器
    ```
    docker-compose up -d nginx mysql redis beanstalkd 
    
    ```
    
 4. 打开项目的.env 文件进行配置    
    ```
    DB_HOST=mysql
    REDIS_HOST=redis
    QUEUE_HOST=beanstalkd 
    
    ```

 5. 与Laradock 平级创建laravel项目
```cgo
    需要映射关系在 laradock下编辑 .env中的 APPLICATION配置项 APPLICATION = ../laravel(项目名)/
    
    相当于项目和docker有软连接 修改映射关系
    
    laradock/nginx/sites/default.conf 中
    
    root /var/www/blog/public
    
    重启Nginx 
    
    docker-compose up -d nginx 
```

  
#### 常见问题
    1. docker 获取images速度过慢超时问题 请更换国内阿里源即可 自己可申请加速。
     vim /etc/docker/daemon.json
        {
          "registry-mirrors": ["https://xxxxx.mirror.aliyuncs.com"]
        }
    2. 更换国内源运行再次报错,查看当前机器时间是否正确 
    
    3. docker 版本与docker-compser 版本兼容
    

 #### 查看更多 [laradock更多支持官网](http://laradock.io/documentation/)
    