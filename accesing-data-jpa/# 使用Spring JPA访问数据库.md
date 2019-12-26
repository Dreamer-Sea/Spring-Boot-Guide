# 使用Spring JPA访问数据库
[toc]
## 构建自己的CrudRepository接口，并在接口中声明自己的数据库操作方法
```java
public interface CustomerRepository extends CrudRepository<Customer, Long> {

    List<Customer> findByLastName(String lastName);

    Customer findById(long id);
}
```
## 注解
将当前的方法声明为Bean，并将它交由Spring IoC容器管理。
```java
@Bean
    public CommandLineRunner demo(CustomerRepository repository){
        // 省略具体实现
    }
```
Bean对象能够通过ApplicationContext的getBean方法获取到。
