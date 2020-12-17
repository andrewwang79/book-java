# 质量性能

## 质量
| 技术 | 采用 | 说明 |
| :----: | ---- | ---- |
| 后端代码质量 | Sonar |  |
| 后端单元测试 | JUnit |  |
| 前端代码质量 | ESlint |  |
| 前端单元测试 | QUnit |  |

###  工具
* eclipse插件：Checkstyle, FindBugs, PMD, [阿里Java代码规约插件](https://segmentfault.com/a/1190000011730490)
### 参考
* [常用 Java 静态代码分析工具的分析与比较](https://www.ibm.com/developerworks/cn/java/j-lo-statictest-tools/)
* [在阿里云环境下搭建基于SonarQube的自动化安全代码检测平台](https://yq.aliyun.com/articles/357247)

## 性能
### 分析工具
* [JDK工具](https://www.cnblogs.com/z-sm/p/6745375.html)
* [jmap -histo pid 输出的对象](https://blog.csdn.net/lxb_champagne/article/details/18352945)
* [jvm调优工具分析指南](https://juejin.im/entry/6844903501269729288)
#### 使用
```
jmap heap 1
jmap -histo 1 > 1.txt
jmap –histo:live [pid] // 查看内存分配命令(可以看到大量占用内存的对象)
jmap -dump:file=文件名.dump [pid]
jcmd 1 GC.run
docker-compose文件里需设置启用jdk工具:
cap_add:
  - SYS_PTRACE
```

#### visualvm
外部工具
* [visualvm](https://visualvm.github.io/)
* [Jstatd方式远程监控Linux下 JVM运行情况](http://www.cnblogs.com/catkins/p/5970364.html)

#### JavaMelody
内置到项目
* [JavaMelody](https://github.com/javamelody/javamelody)
* [Spring Boot集成](https://github.com/javamelody/javamelody/tree/master/javamelody-for-spring-boot)

### troubleshooting
* [远程调试(一般用于开发环境)](http://chainhou.iteye.com/blog/1837059)
  1. java -Dfile.encoding=UTF8 -Duser.timezone=GMT+08 -Xdebug -Xrunjdwp:server=y,transport=dt_socket,address=8888,suspend=n -jar abc.jar
  1. Idea配置Remote调试
* [Java程序员必备：常见OOM异常分析](https://juejin.im/post/6844903957920219143)
* [Java进程崩溃分析](https://blog.csdn.net/wangchaox123/article/details/100658938)

### 资料
## 执行命令
* 指定log配置文件执行jar，jar必须放最前面。[参考](http://tengj.top/2017/04/05/springboot7/) : java -jar abc.jar -Xmx200m --logging.config=abc/logback.xml
* [高手教大家如何配置JVM参数](http://developer.51cto.com/art/200907/135160.htm)
* [JMX学习笔记](https://www.jianshu.com/p/414647c1179e)
