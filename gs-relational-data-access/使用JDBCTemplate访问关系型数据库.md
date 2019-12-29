# 使用JDBCTemplate访问关系型数据库
- [使用JDBCTemplate访问关系型数据库](#--jdbctemplate--------)
  * [在pom.xml文件中加入依赖](#-pomxml-------)
  * [应用了Java 8的新功能](#---java-8----)
    + [Stream](#stream)
    + [forEach](#foreach)
[toc]
## 在pom.xml文件中加入依赖
JDBC和H2数据库。
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jdbc</artifactId>
</dependency>

<dependency>
    <groupId>com.h2database</groupId>
    <artifactId>h2</artifactId>
    <scope>runtime</scope>
</dependency>
```

## 应用了Java 8的新功能
### Stream
```java
List<Object[]> splitUpNames = Arrays.asList("John Woo", "Jeff Dean", "Josh Bloch").stream()
                .map(name -> name.split(" "))
                .collect(Collectors.toList());
```
将三个姓名先转为Arrays中的List格式然后将其stream化，并将原来的元素映射为新元素然后存储在一个新的List中。
### forEach
```java
jdbcTemplate.query("SELECT id, first_name, last_name FROM customers WHERE first_name = ?",
                new Object[]{"Josh"}, (rs, rowNum) -> new Customer(rs.getLong("id"), rs.getString("first_name"), rs.getString("last_name"))
        ).forEach(customer -> log.info(customer.toString()));
```
将查询到的结果用customer表示，然后在日志信息中输出。