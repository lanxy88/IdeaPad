# 国图大云
采用微服务实现的国图应用服务框架，以轻量化Restful标准定义服务接口，统一应用与服务边界，提供一致性跨语言的应用解决方案。

## 云服务治理框架内涵

- 云服务技术标准
- 云服务注册中心
- 云服务调用追踪
- 云服务日志管理
- 云服务网关
- 异构云服务注册
- 容器管理
- 应用模板管理
- 主机管理
- 镜像库管理

## 核心云服务
国图大云除提供标准技术方案还提供基础云服务，包括：

- 统一授权认证中心
- 资源共享中心
- 文档管理中心
- 全文索引
- 消息服务
- 工作流引擎
- 表单服务
- 行政区区划服务
- 开发中心

## 基于框架如何实现基础云服务
### 1.新建Maven工程，POM中设置parnet、添加依赖、设置编译方式
```xml
    <parent>
        <artifactId>parent</artifactId>
        <groupId>cn.gtmap.gtcc</groupId>
        <version>1.0-SNAPSHOT</version>
    </parent>
```
```xml
    <dependencies>

        <dependency>
            <groupId>cn.gtmap.gtcc</groupId>
            <artifactId>gtmap-cloud-app-starter</artifactId>
            <version>1.0-SNAPSHOT</version>
        </dependency>

        <!-- additional -->

    </dependencies>
```
```xml
    <build>
        <plugins>
            <!-- important -->
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-antrun-plugin</artifactId>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-assembly-plugin</artifactId>
            </plugin>
            <!-- important -->

            <!-- additional -->

        </plugins>
    </build>
```
### 2.新建主入口类，注解 @GTMapCloudApplication 
```java
@GTMapCloudApplication
public class App {

    public static void main(String[] args) {
        SpringApplication.run(App.class, args);
    }

}
```
### 3.添加配置文件，设置相关配置参数，添加自定义参数配置
```bash
application.yml
bootstrap.yml
logback.xml
banner.txt
```
### 4.拷贝build内容（工程编译打包方式）
```bash
.bin/docker-compose.yml
.bin/Dockerfile
.bin/image-build.bat
.bin/image-push.bat
.bin/start.bat
.bin/start.sh
assembly.xml
```
### 5.主入口运行启动应用
### 6.编译打包
```bash
mvn clean package
```
## 使用授权认证框架云服务实现
### 1.Maven dependency 改为：
```xml
        <dependency>
            <groupId>cn.gtmap.gtcc</groupId>
            <artifactId>gtmap-cloud-app-security-starter</artifactId>
            <version>1.0-SNAPSHOT</version>
        </dependency>
```
### 2.主入口应用注解改为 @GTMapSecurityApplication：

