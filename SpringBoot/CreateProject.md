# 从零创建一个 SpringBoot 项目

## 系统环境配置

这里以 vscode 为例 其他自己熟悉的 IDE 也行  
首先确保自己的环境有自己需要的 jdk 与 maven（Java 构建工具）  
这里以 linux Ubuntu 系统为例

```
apt-get install openjdk21-jdk
apt-get install maven
```

然后输入以下命令判断是否成功安装到系统环境内

```
java --version
mvn -v
```

输出以下结果就是安装好了

```
openjdk 21.0.4 2024-07-16
OpenJDK Runtime Environment (build 21.0.4+7-Ubuntu-1ubuntu224.04)
OpenJDK 64-Bit Server VM (build 21.0.4+7-Ubuntu-1ubuntu224.04, mixed mode, sharing)
```

```
Apache Maven 3.8.7
Maven home: /usr/share/maven
Java version: 21.0.4, vendor: Ubuntu, runtime: /usr/lib/jvm/java-21-openjdk-amd64
Default locale: en_US, platform encoding: UTF-8
OS name: "linux", version: "5.15.153.1-microsoft-standard-wsl2", arch: "amd64", family: "unix"
```

## 编辑器插件

其他系统同理 只要能找到环境变量就行  
接下来在 vscode 内安装对应插件

- Debugger for Java

* Extension Pack for Java

- Language Support for Java(TM) by Red Hat

* Maven for Java

- Spring Boot Dashboard

* Spring Boot Extensions Pack
* Spring Boot Tools

- Spring Initializr Java Support

* Test Runner for Java

## 创建项目

首先按住 Ctrl+Shift+P 打开命令
输入 Create a Maven Project  
根据需求选择自己需要的配置

## 构建热部署

打开 pom.xml 文件 点击添加依赖选择 DevTools 添加

##
