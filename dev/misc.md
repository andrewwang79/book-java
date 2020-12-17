# 知识

## 资料
* ﻿[﻿Java多线程之ReentrantLock与Condition](https://www.cnblogs.com/xiaoxi/p/7651360.html)
* [ThreadLocalMap里Entry为何声明为WeakReference](https://cloud.tencent.com/developer/article/1125219)
* [Java参数](https://docs.oracle.com/javase/7/docs/technotes/tools/windows/java.html)
* [JMX学习笔记](https://www.jianshu.com/p/414647c1179e)
* [RSA与AES混合加密算法的实现](https://blog.csdn.net/jkxqj/article/details/25228707)
* [JSch连接交互式shell+输出流重定向](https://www.dazhuanlan.com/2019/09/28/5d8e4f2219ba4/)

## 类型处理
* 值类型(long)和引用类型(Long)的区别。值类型比较用==，引用类型比较必须用equal。
* Boolean的变量定义不要有is，如isOn用on。表结构字段还是要有is.[参考](http://www.learndiary.com/2006/11/%E5%9C%A8eclipse%E4%B8%ADjavabean%E4%B8%AD%E7%9A%84boolean%E5%9E%8B%E5%8F%98%E9%87%8F%E4%B8%8D%E8%A6%81%E7%94%A8is%E5%BC%80%E5%A4%B4/)
* BigDecimal的相等比较。
scale(小数点后数量)的不同，compareTo忽略scale，equals要比较scale
```java
BigDecimal bd1 = new BigDecimal("1.00");
Assert.assertFalse(BigDecimal.ONE.equals(bd1));
Assert.assertTrue(BigDecimal.ONE.compareTo(bd1) == 0);
```

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
