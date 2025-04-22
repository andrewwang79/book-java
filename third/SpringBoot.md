# SpringBoot
* [关闭](http://tech.dianwoda.com/2017/12/18/chang-jian-javaying-yong-you-ya-guan-bi/)

## Security
* [SpringBoot配置属性之Security](https://segmentfault.com/a/1190000004309242)

## MQ
* [SpringBoot配置属性之MQ](https://segmentfault.com/a/1190000004309900)

## Actuator
* [SpringBoot四大神器之Actuator](https://segmentfault.com/a/1190000004318360)

## 启动
```--spring.profiles.active=prod --spring.config.location=./application.yml```

## 配置
* [配置参数](https://docs.spring.io/spring-boot/docs/current/reference/html/common-application-properties.html)
* [多环境配置](https://docs.spring.io/spring-boot/docs/current/reference/html/howto-properties-and-configuration.html)

```
spring:
	profiles: development
server:
	port: 9001

spring:
	profiles: production
server:
	port: 9002
```

## jar包的文件操作
```
cd ${path} jar xf "${jar_file}" # 解压jar包path

mkdir -p "${path}/META-INF"
将文件列表放到META-INF目录

(cd "${path}" && jar cf ${jar_file} .) # 重新打包JAR文件
```

## 使用
### 启动时创建表结构
* 属性文件的属性spring.jpa.hibernate.ddl-auto
* auto是创建，none是不创建
* 建议多用none，可以节省启动时间

### service初始化
```java
@PostConstruct
private void init() {
}
```

### 属性值设置
```java
@Value("${prop}") // 必须在属性文件设置
@Value("${prop:}") // 有默认值，如字符空
@Value("${prop:hello}") // 设置默认值是hello，属性文件优先
String prop = "hi"; // 赋值是无效的
```

### entity注意事项
#### 日期显示处理，API返回和緩存保存都会生效
```java
@JsonFormat(shape = JsonFormat.Shape.STRING, pattern = DateUtils.DateTimeFormat)
public Date getCreatetime() {}
```

### RestController对象设置
#### POST
@RequestBody User user

@RequestBody接收的对象定义规则，否则函数会异常（无法响应）
1. 必须要有默认构造函数
1. 如有子类，其在接收类的变量定义必须是static
也可以直接接收String，如@RequestBody String data

#### GET
```java
url路径参数：@PathVariable String entity

querystring参数：@RequestParam("data") String data
```

### 创建分页Page

```java
, @RequestParam int pageIndex, @RequestParam(defaultValue = "10") int pageSize
new PageImpl<Order>(pl, new PageRequest(pageIndex, pageSize), total)
```

### jpa分页的返回对象转换

```java
Page<Source> sourcePage = null;
Page<Target> = sourcePage.map(new Converter<Source, Target>() {
               @Override
               public Target convert(Source source) {
                    return new Target(source);
               }
          });
```

### JPA多表查询

```java
@Query("SELECT t FROM CmsArticle t, CmsCategory u WHERE t.categoryId=u.id AND t.status=:status AND u.code=:code AND u.parentId is null AND u.status=:status")
    public Page<CmsArticle> searchByCategory(@Param("code") String code, @Param("status") int status, Pageable pageable);
```

* [JPA单表/多表搜索](http://blog.csdn.net/lsk12162012/article/details/50442792)，对象要有关联（不推荐本方案）

### 缓存
* 不需要定义key，key是有规则生成的。函数参数必须是Object类型
* @Cacheable(value = "ProductListByCategory")
* 如果返回值是列表，则必须定义具体列表，如ArrayList，绝对不能使用List。
* 同一个类的函数调用是不能启用缓存的（即缓存无效）

### API接口获取请求用户的类对象
* [HandlerMethodArgumentResolver用于统一获取当前登录用户](https://www.cnblogs.com/myseries/p/12819849.html)
```java
@RequestMapping("/apiX")
public Response apiX(@CurrentUser User user)
```

### 初始化时注入调用库的类对象
```java
// 调用库内预置逻辑，谁调用谁配置参数
@Configuration
public class MyConfig {
  @Bean
  public AbcConfig abcConfig() {
    AbcConfig cfg = new AbcConfig();
    cfg.setProductName("demo");
    return cfg;
  }
}
```

# 资料
* [Spring Resource之内置的Resource实现](http://www.cnblogs.com/zhangminghui/p/4376424.html)
* [Jackson Exceptions – Problems and Solutions](http://www.baeldung.com/jackson-exception)
* [JPA手册，含命名规范](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/)
* [JPA使用](https://www.jianshu.com/p/0cb0ffe07b16)
* [SpringMVC异常处理详解](http://www.cnblogs.com/xinzhao/p/4902295.html)