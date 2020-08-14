# 其他
## JVM
1. [JVM运行时数据区(Run-TimeDataAreas)及内存结构](https://www.cnblogs.com/wuzhenzhao/p/12346515.html)
1. [JVM的底层实现原理](https://blog.csdn.net/fangqun663775/article/details/54572635)
1. [Java JVM 运行机制及基本原理](https://zhuanlan.zhihu.com/p/25713880)

1. minor GC : Eden的存活对象拷贝到某个Survivor Space, 当Survivor Space空间满了后, 剩下的live对象就直接拷贝到老一代中。每次GC后，Eden内存块会被清空。
1. JVM命令执行的工作原理
```
C/C++的工作原理：先将语句转化为汇编，再把汇编转换为二进制命令传给CPU
Java：编译成.class文件（字节码文件），JVM把字节码文件解析成汇编和二进制命令。
```

## 知识
1. [ThreadLocalMap里Entry为何声明为WeakReference](https://cloud.tencent.com/developer/article/1125219)

## 类型
1. 值类型(long)和引用类型(Long)的区别。值类型比较用==，引用类型比较必须用equal。
1. Boolean的变量定义不要有is，如isOn用on。表结构字段还是要有is.[参考](http://www.learndiary.com/2006/11/%E5%9C%A8eclipse%E4%B8%ADjavabean%E4%B8%AD%E7%9A%84boolean%E5%9E%8B%E5%8F%98%E9%87%8F%E4%B8%8D%E8%A6%81%E7%94%A8is%E5%BC%80%E5%A4%B4/)
1. BigDecimal的相等比较。
scale(小数点后数量)的不同，compareTo忽略scale，equals要比较scale
```java
BigDecimal bd1 = new BigDecimal("1.00");
Assert.assertFalse(BigDecimal.ONE.equals(bd1));
Assert.assertTrue(BigDecimal.ONE.compareTo(bd1) == 0);
```

## 技术
[RSA与AES混合加密算法的实现](https://blog.csdn.net/jkxqj/article/details/25228707)

## CSV(excel)
* http://opencsv.sourceforge.net/
* https://www.callicoder.com/java-read-write-csv-file-opencsv/
* http://zetcode.com/articles/opencsv/
* https://www.geeksforgeeks.org/writing-a-csv-file-in-java-using-opencsv/

## SCP
* https://github.com/hierynomus/sshj/blob/762d088388667ec29eb7c81c725b33f0f3cffe78/src/main/java/net/schmizz/sshj/SSHClient.java
```java
client.authPassword(username, password);
final Session session = client.startSession();
try {
  final Command cmd = session.exec(true);
  cmd.join(1, TimeUnit.SECONDS);
} finally {
  session.close();
}
```

## FTP
* https://www.jianshu.com/p/d4c6f3ec56d5
* https://blog.csdn.net/u012506466/article/details/73558134
* https://blog.csdn.net/weixin_36907025/article/details/77152446
