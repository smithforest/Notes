# SpringBoot基础篇

## SpringBoot搭建

1. IDEA从SpringBoot官网直接搭建 
2. IDEA从阿里云官网直接搭建
3. 手工从SpringBoot官网搭建，然后倒入坐标
4. 搭建maven空项目，导入pom.xml(maven管理可能需要手动添加项目)

## SpringBoot配置文件详解

1. parent 用于指定依赖版本，防止版本冲突

   ```xml
   <parent>
       <groupId>org.springframework.boot</groupId>
       <artifactId>spring-boot-starter-parent</artifactId>
       <version>2.7.8</version>
       <relativePath/> <!-- lookup parent from repository -->
   </parent>
   ```

2.  starter 用于导入项目需要的依赖包，减少依赖配置

   ```xml
   <dependencies>
       <dependency>
           <groupId>org.springframework.boot</groupId>
           <artifactId>spring-boot-starter-web</artifactId>
       </dependency>
   
       <dependency>
           <groupId>org.springframework.boot</groupId>
           <artifactId>spring-boot-starter-test</artifactId>
           <scope>test</scope>
       </dependency>
   </dependencies>
   ```

4. Springboot引导类

```java
@SpringBootApplication
public class Springboot0103QuickstartApplication {

    public static void main(String[] args) {
        SpringApplication.run(Springboot0103QuickstartApplication.class, args);
    }
}
```

  其中 SpringApplication得到的是一个是spring管理bean的上下文容器。

```java
ConfigurableApplicationContext configurableApplicationContext = SpringApplication.run(Springboot0103QuickstartApplication.class, args);
configurableApplicationContext.getBean(BookController.class)
```

4. tomcat服务器

   tomcat本质也是Java对象，将tomcat交给spring容器进行管理。

   maven排除tomcat依赖，并添加jetty服务器

   ```xml
           <dependency>
               <groupId>org.springframework.boot</groupId>
               <artifactId>spring-boot-starter-web</artifactId>
               <exclusions>
                   <exclusion>
                       <groupId>org.springframework.boot</groupId>
                       <artifactId>spring-boot-starter-tomcat</artifactId>
                   </exclusion>
               </exclusions>
           </dependency>
   
           <dependency>
               <groupId>org.springframework.boot</groupId>
               <artifactId>spring-boot-starter-jetty</artifactId>
           </dependency>
   ```

Jetty比tomcat更轻量级，可扩展性更强，谷歌应用引擎就用的jetty

springboot用的三大服务器：tomcat，jetty（负载远比不上tomcat ），undertow

5. springboot 配置文件

   springboot配置文件支持application.properties,application.yml(主流)，application.yaml(加载顺序也是这个顺序)。

   properties配置文件格式如下：

   ```properties
   server.port=8081
   logging.level.root=debug
   ```

   yml和yaml配置文件格式如下：

   ```yml
   server:
     port: 8082
   logging:
     level:
       root: error
   ```

   springboot的配置文件一般在resources文件夹下面。

   IDEA手动添加配置文件的方式：project structure ->facets->项目名->配置文件标识->+号

   yaml数据格式，和xml，properties一样都只是一种存储数据的文件格式。一般以.yml和.yaml结尾。

   

## REST知识补充

REST (respresentational state transfer) 表现形式转换

 根据REST风格对资源进行访问成为RESTFUL

描述模块的名称通常使用复数，也就是i加s的格式描述，表示此类资源，而非单个资源，例如：users，books。 

@RestController=@responsebody+@controller