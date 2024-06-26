# Maven

* [Maven生成可以直接运行的jar包的多种方式](https://blog.csdn.net/xiao__gui/article/details/47341385)
* [Maven的Snapshot/Release打包上传](https://blog.csdn.net/crowhyc/article/details/76204315)
```
snapshot发布命令
mvn deploy
release发布命令
mvn release:prepare
mvn release:perform
```
* 库类型的jar包(非运行包)，不要用插件[spring-boot-maven-plugin](http://chace0120.github.io/2016/05/13/Maven%E9%A1%B9%E7%9B%AE%E5%A4%9A%E6%A8%A1%E5%9D%97%E7%9A%84%E6%89%93%E5%8C%85/)
* [application.properties 改成 application.yml](http://blog.csdn.net/u012922706/article/details/69664987)
* Windows本地仓库默认地址是"C:\Users\\[用户名]\\.m2\\repository\"
* Linux: 本地仓库默认地址是"[用户名]/.m2/", 配置文件是"/usr/share/maven/conf/settings.xml"
* jar无法重新再下的处理：删除本地仓库里对应的"*.lastUpdated"。
* Maven私有仓库：Nexus
* pom.xml上加仓库定义
```
<repositories>
    <repository>
        <id>maven-xyz</id>
        <name>Maven swao Mirror</name>
        <url>http://mvn.xyz.com/nexus/content/repositories/thirdparty/</url>
        <releases>
            <enabled>true</enabled>
        </releases>
        <snapshots>
            <enabled>false</enabled>
        </snapshots>
    </repository>
</repositories>
```

* 阿里源配置(settings.xml)
```
<mirror>
    <id>alimaven</id>
    <mirrorOf>central</mirrorOf>
    <name>Aliyun Central</name>
    <url>https://maven.aliyun.com/repository/central</url>
</mirror>
```

## yml
1. 使用内置函数
  1. str: ${random.value} # 32位的随机字符串
  1. uuid: ${random.uuid} # uuid
  1. num1: ${random.int(100)} # 100内随机整数
  1. num2: ${random.int(0,99)} # 0-99内的随机整数
1. 使用yml定义的变量
  * url: ${th.const.server}
  * url: tcp://${th.const.server}:12345
1. 使用环境变量
  * path: ${M2_HOME:abc} # 设置成环境变量环境变量，如没有则使用默认值"abc"
