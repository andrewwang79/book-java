# 集合

1. list到map
```java
Map<String, Company> objMap = list.stream().collect(Collectors.toMap(Company::getCode, (obj) -> obj));
```

1. 循环处理(java8)
```java
// 方法1
List<User> userList = Lists.newArrayList();
originList.forEach((party)->userList.add(new User(party)));

// 方法2，同时可以支持filter(过滤出需要返回的)
List<String> userNameList = originList.stream().map(obj -> {
return obj.getName();
}).collect(Collectors.toList());

```
Map也可以同样循环处理

## list
1. 字符串[]到list
```java
List<String> stooges = Arrays.asList("Larry", "Moe", "Curly");
Arrays.asList(new String[] {"Larry", "Moe", "Curly"})
```

1. list到字符串
```java
Joiner.on(",").join(list);
```

1. 字符串到list
```java
Splitter. on("," ).omitEmptyStrings().splitToList("sd,dsf");
```

1. 比较
```java
Collections.sort(listA, new Comparator<Class4Sort>() {
	  public int compare(Class4Sort s1, Class4Sort s2) {
	      // 升序排的话就是第一个参数.compareTo(第二个参数), 降序排的话就是第二个参数.compareTo(第一个参数)
	      return s2.getNumber().compareTo(s1.getNumber());
	  }
}
```

## map
1. map到字符串
```java
Map<String, String> map = this.getRequestParams(request);
String body = Joiner.on("&").withKeyValueSeparator("=").join(map);
```

1. 字符串到map
```java
final Map<String, String> join =Splitter.on("&").withKeyValueSeparator("=").split("id=123&name=green");
```

1. map循环
```java
for (Map.Entry<String, String> entry : params.entrySet()) {
		String.format("%s=[%s]", entry.getKey(),entry.getValue());
}
允许删除
// Map<String, Integer>
Iterator it = map.keySet().iterator();
while (it.hasNext()) {
    String key = (String) it.next();
    Integer val = map.get(key);
    if (val < 100) {
        it.remove();
    }
}
```

1. 初始化map
```java
ImmutableMap.<String, String>builder().put("uri", uri).put("body", body).build();
####从一个list生成另外一个list（Advertise转换成ClientBanner）
Lists.transform(listAdv, new Function<Src, Target>() {
    @Override
    public Target apply(Src src) {
         return new Target(src);
    }
});
```
