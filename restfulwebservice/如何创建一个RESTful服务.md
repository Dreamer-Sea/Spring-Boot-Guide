# 如何创建一个RESTful服务
[toc]
## 代码示例
```java
@RestController
public class GreetingController {
    private static final String template = "Hello, %s!";
    private final AtomicLong counter = new AtomicLong();

    @RequestMapping("/greeting")
    public Greeting greeting(@RequestParam(value = "name", defaultValue = "World") String name){
        return new Greeting(counter.incrementAndGet(),
                String.format(template, name));
    }
}
```
## 注解
### @RequestMapping
这是一个“请求映射”的注解，它将URL与具体方法捆绑实现，通过访问URL就能够调用相应的方法。该注解可以指定请求方式(例如：GET，PUT或POST)，@RequestMapping(method=GET)。
### @RequestParam
“请求参数”注解，表示该参数是由URL传入，URL中的参数名由value指定，defaultValue表示默认传入的值。
### @RestController
这是从Spring 4才开始有的注解，该注解表示修饰的类返回一个域对象(Domain Object)，相当于@Controller和@ResponseBody的结合。
### @SpringBootApplication
该注解表示该类是整个Spring Boot程序的入口。它是多个注解的集合(@Configuration，@EnableAutoConfiguration，@ComponentScan)。


Spring Boot默认带有Jackson 2库，该库能够将Java Object对象转为JSON格式。

