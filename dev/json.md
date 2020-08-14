# json

* 转换成json格式文本(JsonObject)
```java
User obj;
// String jsonText = new Gson().toJson(obj);
String jsonText = JSONUtils.toJson(obj, User.class, false);
```

* 转换成类对象(JsonObject, json格式文本)
```java
User user = JSONUtils.fromJsonObject(jsonObject, User.class, null);
// User user = new GsonBuilder().create().fromJson(jsonText, User.class);
User user = JSONUtils.fromJson(jsonText, User.class);
```

* 转换成数组对象(json格式文本)

```java
// 获取特定对象列表
List<Person> rtn =JSONUtils.fromJson(jsonText, new TypeToken<List<Person>>(){}.getType());

ArrayList<String> list = JSONUtils.fromJson(jsonText, ArrayList.class);

// 默认序列化有问题(map里的number会转成double)
// 获取对象列表，对象是个map，和json的对象值一一对应。
jsonText = "[{id:123,name:'第三方',price:8.88}]";
ArrayList<Map<String, Object>> list = JSONUtils.fromJson(jsonText, ArrayList.class, ArrayList.class, new ListMapJsonDeserializer());
```

* 转换成Map对象(json格式文本)

```java
Map<Integer,Person> map =JSONUtils.fromJson(jsonText, new TypeToken<Map<Integer,Person>>(){}.getType());

jsonText = "{id:123,name:'第三方',price:8.88}";
Map<String, Object> map = JSONUtils.fromJson(jsonText, HashMap.class, HashMap.class, new MapJsonDeserializer());

// com.fasterxml.jackson.databind
ObjectMapper objectMapper = new ObjectMapper();
Map<String, Object> map = objectMapper.readValue(jsonText, Map.class);
```

*  转换成JsonObject(json格式文本)
```java
JsonObject jo = JSONUtils.parse(jsonText);
JsonArray ja = JSONUtils.parseArray(jsonText);
```

* 创建json对象
```java
JsonObject jo = new JsonObject();
jo.add("list", JSONUtils.toJsonElement(list));
jo.add("obj", JSONUtils.toJsonElement(obj));
jo.add("value", new JsonPrimitive(val));
```
