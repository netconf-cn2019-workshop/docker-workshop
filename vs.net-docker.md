# Visual Studio.NET 2019 Container Tools

Visual Studio 2019对Docker和Kubernetes的支持有限, 需要安装Microsoft Azure的工作负载

1. 在项目仲添加 Container Tools reference

```bash
   dotnet add package Microsoft.VisualStudio.Azure.Containers.Tools.Targets
```

2. 添加 `msbuild` 支持 Docker image

```xml

  <PropertyGroup Label="Docker Variables">
    <PAT>secret</PAT>
    <FEED>feed</FEED>
    <!-- change this value if the port is different -->
    <MSI_ENDPOINT>http://host.docker.internal:5050/oauth2/token</MSI_ENDPOINT>
    <MSI_SECRET>19603b25-f198-4156-a82a-b68d40681455</MSI_SECRET>
  </PropertyGroup>

  <PropertyGroup Label="Docker Container Configurations">
      <!--https://docs.microsoft.com/en-us/visualstudio/containers/container-msbuild-properties?view=vs-2019-->
    <DockerfileContext>../../.</DockerfileContext>
    <DockerfileFile>../../src/K8.FrontEnd/Dockerfile</DockerfileFile>
    <DockerfileBuildArguments>--build-arg PAT=$(PAT) --build-arg FEED=$(FEED) --build-arg MSI_ENDPOINT=$(MSI_ENDPOINT) --build-arg MSI_SECRET=$(MSI_SECRET)</DockerfileBuildArguments>
    <DockerfileRunArguments>-e MSI_ENDPOINT=$(MSI_ENDPOINT) -e MSI_SECRET=$(MSI_SECRET)</DockerfileRunArguments>
    <DockerDefaultTargetOS>Linux</DockerDefaultTargetOS>
  </PropertyGroup>

```

## 参考

- [Container Tools build properties](https://docs.microsoft.com/zh-cn/visualstudio/containers/container-msbuild-properties?view=vs-2019)

- [Docker Compose build properties](https://docs.microsoft.com/zh-cn/visualstudio/containers/docker-compose-properties?view=vs-2019)
