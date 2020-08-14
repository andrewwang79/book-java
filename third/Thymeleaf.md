# Thymeleaf

## 资料
* [介绍](http://www.tianmaying.com/tutorial/using-thymeleaf)
* [Spring MVC中使用Thymeleaf模板引擎](https://www.tianmaying.com/tutorial/spring-mvc-thymeleaf)

## 使用
1. 不重启编辑网页：设置成cache=false

1. URL的处理是通过语法@{...}来处理
```
<a th:href="@{http://www.thymeleaf.org}">Thymeleaf</a>
```

1. 字符串替换
  * 局部：```<span th:text="|Welcome to our application, ${user.name}!|">     th:href="|mailto:${text_email}|"```
  * 全部：```th:href="${jsFile}"```

1. 自定义属性
  1. ```<div th:attr="selfdefineAttr=${xxx}"></div>```
  1. ```<div th:attr="style='background-image:url('+${banner.pic}+')'"></div>```
  1. ```<div th:style="'background-image:url('+${banner.pic}+')'"></div>```

1. 直接显示html
  1. ```<div th:remove="tag" th:utext="${content}"></div>```
  1. ```<%==content%>```。单个=是值，两个=是html显示
