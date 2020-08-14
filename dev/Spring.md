# Spring

## 启动时创建表结构
* 属性文件的属性spring.jpa.hibernate.ddl-auto
* auto是创建，none是不创建
* 建议多用none，可以节省启动时间

## service初始化
```java
@PostConstruct
private void init() {
}
```

## 属性值设置
```java
@Value("${prop}") // 必须在属性文件设置
@Value("${prop:}") // 有默认值，如字符空
@Value("${prop:hello}") // 设置默认值是hello，属性文件优先
String prop = "hi"; // 赋值是无效的
```

## entity注意事项
### 日期显示处理，API返回和緩存保存都会生效
```java
@JsonFormat(shape = JsonFormat.Shape.STRING, pattern = DateUtils.DateTimeFormat)
public Date getCreatetime() {}
```

## RestController对象设置
### POST
@RequestBody User user

@RequestBody接收的对象定义规则，否则函数会异常（无法响应）
1. 必须要有默认构造函数
1. 如有子类，其在接收类的变量定义必须是static
也可以直接接收String，如@RequestBody String data

### GET
url路径参数：@PathVariable String entity

querystring参数：@RequestParam("data") String data

## 创建分页Page<Object>
```java
, @RequestParam int pageIndex, @RequestParam(defaultValue = "10") int pageSize
new PageImpl<Order>(pl, new PageRequest(pageIndex, pageSize), total)
```

## jpa分页的返回对象转换
```java
Page<Source> sourcePage = null;
Page<Target> = sourcePage.map(new Converter<Source, Target>() {
               @Override
               public Target convert(Source source) {
                    return new Target(source);
               }
          });
```

## JPA多表查询
JPA多表查询
```java
@Query("SELECT t FROM CmsArticle t, CmsCategory u WHERE t.categoryId=u.id AND t.status=:status AND u.code=:code AND u.parentId is null AND u.status=:status")
    public Page<CmsArticle> searchByCategory(@Param("code") String code, @Param("status") int status, Pageable pageable);
```
[JPA单表/多表搜索](http://blog.csdn.net/lsk12162012/article/details/50442792)，对象要有关联（不推荐本方案）

## 缓存
* 不需要定义key，key是有规则生成的。函数参数必须是Object类型
* @Cacheable(value = "ProductListByCategory")
* 如果返回值是列表，则必须定义具体列表，如ArrayList，绝对不能使用List。
* 同一个类的函数调用是不能启用缓存的（即缓存无效）

## 资料
* [Spring Resource之内置的Resource实现](http://www.cnblogs.com/zhangminghui/p/4376424.html)
* [Jackson Exceptions – Problems and Solutions](http://www.baeldung.com/jackson-exception)
* [JPA手册，含命名规范](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/)
* [JPA使用](https://www.jianshu.com/p/0cb0ffe07b16)
