# 常用

1. 异常
  * UnsupportedOperationException

1. 日志
```java
log.info(LogUtils.gen("message", "key1", value1, "key2", value2));
log.info(LogUtils.gen("getUser", ImmutableMap.<String, String> builder().put("token", token).put("userId", userId).build()));
```

1. 对象克隆
```java
// 一般是从parent克隆出child
BeanUtils.copyProperties(parent, child);
```

1. 线程
```java
 new Thread(new Runnable() {
                @Override
                public void run() {
                    // code here
                    }
                }
            }).start();
```

1. (泛型/模板)类/函数
```java
class Demo<T> // 类定义
{
    public void show(T t) {}
}
Demo<String> d1 = new Demo<String>(); // 调用

public <T> void test(T t) {} // 函数定义
test(new ClassA()); // 调用
```

1. 回调函数（Java8的功能）
```java
public void callbackUsage(Function<String, String> fn) {
    fn.apply(“123”);
}
this.callbackUsage(new Function<String, String>() {
    @Override
    public String apply(String t) {
        return null;
    }
});
```

1. 注解类获取
```java
this.getClass().isAnnotationPresent(BizApi.class); // 获取所有引用的判断：BizApi是annotation
```

1. bean获取

```java
this.service = this.context.getBean(IUserAccountService.class);

for (Map.Entry<String, Object> entry : this.context.getBeansWithAnnotation(BizApi.class).entrySet()) {
            this.apiMap.put(entry.getKey(), (IBizApi) entry.getValue());
}
```

## 文件系统
1. 组合路径
```java
Path path = Paths.get("path1",  "path2", "fileName");
File file = path.toFile();
```
