# docker-workshop
 .NET Docker 工作坊

#议程

* 前提条件
* Docker基本命令
* 构建自己的镜像
* Docker Hub和私有仓库
* 在云端运行容器
* Docker Compose 和 容器编排

# 前提条件
 
您在计算机上安装了以下软件：
*  Docker Daemon或简称Docker
* .NET Core 2.2+ SDK
* 代码编辑器，例如Visual Studio，VS Code。Visual Studio 不是必需的，但在整个Workshop 中可能会使用

要在Windows上安装Docker，请点击此链接[Docker For Windows](https://docs.docker.com/docker-for-windows/)

# Docker基本命令

每个参与者必须了解Docker背后的基本命令和概念，我写过一篇文章,可以很好的理解Docker基础，以及基本/经过整理的命令列表，请花点时间阅读它：[.NET Core：入门的最简单方法](https://github.com/geffzhang/QcloudNetCore/blob/master/1%20docker/1.dotnetdockerbasic.md)

# 构建自己的镜像 

在Fork 此仓库的根目录中，运行下面的命令：

```
docker build --pull -t aspnetapp .
docker run --name aspnetcore_sample --rm -it -p 8000:80 aspnetapp
```

在应用程序启动时，您应该看到以下控制台输出：

```
>docker run --name aspnetcore_sample --rm -it -p 8000:80 aspnetapp
Hosting environment: Production
Content root path: /app
Now listening on: http://[::]:80
Application started. Press Ctrl+C to shut down.
```
更多内容可以参看: https://github.com/geffzhang/QcloudNetCore/blob/master/1%20docker/3.buildingnetdockerimages.md 

# Docker Hub和私有仓库

[Docker Hub](https://hub.docker.com/) 是Docker的官方存储库，它支持公共和私有存储库。大多数基本镜像都是从那里获取的，并由维护该镜像的公司（例如Microsoft，Node等）发布。


# 在云端运行容器


# Docker Compose 和 容器编排

此项目上有一个docker-compose yaml文件，该文件运行并生成aspnet映像，并启动SQL Server容器。本次工作坊后面还有更复杂的微服务应用实例。你可以在根目录下通过docker-compose up来
初步体验一下，关于容器编排的k8s 相关内容参见后面的内容。

## 例子

你可以在这个仓库里找到更多的 Docker 样例 : https://github.com/dotnet/dotnet-docker
