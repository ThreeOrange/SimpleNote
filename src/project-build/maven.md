一、maven介绍
Maven是基于项目对象模型（POM），可以通过一小段描述信息来管理项目的构建、报告和文档的软件项目管理工具。在使用maven前，需要在Apache maven网站下载，然后配置环境变量，此处忽略。
二、目录结构
src
   -main
       -java
           -package
   -test
       -java
           -package
   resources

三、pom.xml格式
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
  
  <modelVersion>4.0.0</modelVersion>
  <groupId>cn.codingxiaxw.seckill</groupId> 主项目标识
  <artifactId>seckill</artifactId> 
  <packaging>war</packaging> 打包方式
  <version>1.0-SNAPSHOT</version> 版本
  <name>seckill Maven Webapp</name> 
  <url>http://maven.apache.org</url>
  
  <dependencies> 依赖
    <dependency>
      <!--3.0的junit是使用编程的方式来进行测试，而junit4是使用注解的方式来运行junit-->
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.11</version>
      <scope>test</scope>
    </dependency>
  </dependencies>

四、maven常用命令
mvn -v 查看maven版本
    complie 编译
    test 测试
    package 打包

    clean 删除target
    install 安装jar包到本地仓库中

    自动创建目录的两种方式
    1.archetype：generate 按照提示进行选择
    2.archetype：generate -DgroupId=组织名，公司网址的反写+项目名
                          -DartifactId=项目名-模块名
                          -Dversion=版本号
                          -Dpackage=代码所存在的包名

五、maven中的坐标和仓库
坐标：构件，如groupId，artifactId，version （类比于购物时的邮件地址）
仓库：用来管理项目的依赖，分为本地仓库与远程仓库
镜像仓库：A仓库提供B仓库一样的功能，预防防火墙，可以更改仓库位置，位于.m2文件夹当中

六、maven的生命周期和插件
完整的项目构建过程包括：清理、编译、测试、打包、集成测试、验证、部署
maven生命周期：clean 清理项目
               default 构建项目
               site 生成项目站点
               三个阶段相互独立

三个阶段又包含多个子阶段
clean 清理项目
   pre-clean 执行清理前的工作
   clean 清理上一次构建生成的所有文件
   post-clean 执行清理后的文件
default 构建项目（最核心）
  compile test package 等
site 生成项目站点，根据pom信息生成项目站点
  pre-site 在生成项目站点前要完成的工作
  site 生成项目的站点文档
  post-site 在生成项目站点后要完成的工作
  site-deploy 发布生成的站点到服务器上
maven的核心并不执行任何具体的构建任务，所有这些任务都交给插件来完成。

七、pom元素解析
project是maven根元素
<groupId>反写的公司网址+项目名</groupId>
<artifactId>项目名+模块名</artifactId>
<!--第一个0表示大版本号，第二个0表示分支版本号，第三个0表示小版本号 0.0.1
snapshot 快照
alpha 内部测试
beta 公测
Release 稳定
GA 正式发布 -->
<version></version>
<!--默认jar ，亦可设置war zip pom -->
<packaging></packaging>
<name></name>
  <url></url>
  <description></description>
  <developers></developers>
  <licenses></licenses>
  <organization></organization>

  <dependencies>
    <dependency>
      <groupId></groupId>
      <artifactId></artifactId>
      <version></version>
      <type></type>
      <scope>test</scope>
      <!--设置依赖是否可选-->
      <optional></optional>
      <!--排除依赖传递列表-->
      <exclusions>
        <exclusion>

        </exclusion>
      </exclusions>
    </dependency>
  </dependencies>
<!--依赖的管理-->
  <dependencyManagement>
    <dependencies>
      <dependency>

      </dependency>
    </dependencies>
  </dependencyManagement>

  <build>
    <!--插件列表-->
    <plugins>
      <plugin></plugin>
    </plugins>
  </build>

  <parent></parent>
  <!--聚合多个maven模块-->
  <modules></modules>
