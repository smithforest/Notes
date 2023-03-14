# 关于在SpringBoot中读取yaml型配置文件数据

## 1.  yaml文件概述

1.  yaml文件一般以yml和yaml文件结尾

2. yaml文件 主要以冒号加空格的方式进行数据存储，层级关系即构成属性对象

   ```yaml
   server:
     port: 8082
   logging:
     level:
       root: error
   
   users: [spring1,spring2,spring3,spring4]
   users2:
     - 1
     - 2
     - 3
     - 4
   users3: [{name:1,age:18},{name:2,age:19}]
   users4:
     -
       name: 1
       age: 18
     -
       name: 2
       age: 19
   datasource:
     name: admin
     password: 123456
     url: https://google.com
     driver: com.ustc.nothing
   ```

## 2. yaml单属性的读取

使用@value注解加explain language 进行读取，形如

```yaml
@Value("${server.port}")
```

## 3. yaml 对象属性的读取

主要使用以下注解进行对象封装

```java
@Data
@Component
@ConfigurationProperties(prefix = "datasource")
```

## 4. 全部对象的读取

```java
@Autowired
private Environment environment;
```

```java
System.out.println(environment.getProperty("datasource.name"));
```