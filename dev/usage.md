# 使用

## 分析工具
* [JDK工具](https://www.cnblogs.com/z-sm/p/6745375.html)
* [jmap -histo pid 输出的对象](https://blog.csdn.net/lxb_champagne/article/details/18352945)

* [Java程序员必备：常见OOM异常分析](https://juejin.im/post/6844903957920219143)
* [Java进程崩溃分析](https://blog.csdn.net/wangchaox123/article/details/100658938)
* [jvm调优工具分析指南](https://juejin.im/entry/6844903501269729288)

```
jmap heap 1
jmap -histo 1 > 1.txt
jmap -dump:file=文件名.dump [pid]
jcmd 1 GC.run
```

docker-compose文件里需设置启用jdk工具
```
cap_add:
  - SYS_PTRACE
```

## 执行命令
1. 指定log配置文件执行jar，jar必须放最前面。[参考](http://tengj.top/2017/04/05/springboot7/) : java -jar abc.jar -Xmx200m --logging.config=abc/logback.xml
1. 远程调试(一般用于开发环境)
  1. java -Dfile.encoding=UTF8 -Duser.timezone=GMT+08 -Xdebug -Xrunjdwp:server=y,transport=dt_socket,address=8888,suspend=n -jar abc.jar
  1. Idea配置Remote调试

## 开发工具
1. 代码编辑器开启窗口Problems(问题)和Outline(类结构)
1. 可以暂时关闭build automatically，但要尽快开启。尽量少用Clean。
1. [Java项目导出可运行的jar文件](https://blog.csdn.net/mahoking/article/details/42871937)
