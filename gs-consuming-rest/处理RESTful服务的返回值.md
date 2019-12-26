# 处理RESTful服务的返回值
[toc]
## 注解
@JsonIgnoreProperties注解来自Jackson库，表示忽略该类中没有绑定的JSON属性。

## 注意
类中的成员变量名必须与JSON属性名一致。如果不一致可以使用@JsonProperty注解来说明。

RestTemplate底层实现是HttpURLConnection。

CommandLineRunner接口能够在项目启动前执行一些初始化操作，ApplicationRunner也能够实现类似的功能。