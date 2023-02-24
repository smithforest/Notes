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