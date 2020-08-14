# SpringCloud

## 系统结构
* 服务注册与发现、服务消费、负载均衡、断路器、智能路由、配置管理等

![](/s/microservice.png)
说明：绿色虚框是SpringCloud的服务，蓝色虚框是业务方工作

## 服务治理系统
* spring boot admin
* 面向开发人员
  * 看服务状态和日志等
  * 服务依赖和调用链。pinpoint
  * 动态路由

## 方案
### 熔断&降级
|  | 触发 | 目的 | 处理方式 |
| :----: | -- | -- | -- |
| 降级 | 压力瞬间剧增 | 降低整体负荷 | 简单/延迟/暂停使用一些不重要/不紧急的服务，释放资源以保证核心交易正常运作或高效运作 |
| 熔断 | 某个下游服务故障 | 防止雪崩效应 | 熔断该节点微服务的调用，快速返回错误的响应信息。当检测到服务调用响应正常后，恢复调用链路 |

https://blog.csdn.net/guwei9111986/article/details/51649240

## 资料
1. [spring-cloud](http://projects.spring.io/spring-cloud/)
1. [spring cloud_百度百科](https://baike.baidu.com/item/spring%20cloud/20269825)
1. Spring Cloud中文网：[1](http://springcloud.cn/)，[2](https://springcloud.cc/)

1. [微服务框架-SpringCloud简介](http://blog.sina.com.cn/s/blog_493a84550102wkp2.html)
1. [SpringCloud分布式开发五大神兽](http://www.cnblogs.com/ilinuxer/p/6580998.html)
1. [springcloud(一)：大话Spring Cloud](http://www.cnblogs.com/ityouknow/archive/2017/05/01/6791221.html)

1. [史上最简单的 SpringCloud 教程](http://blog.csdn.net/forezp/article/details/70148833)
1. [ccblog教程](http://www.ccblog.cn/contentTag.htm?tag_id=94)

### new
* [使用Spring Cloud构建统一配置中心](https://www.jianshu.com/p/69dea19abf04)
https://blog.csdn.net/Ay_Ly/article/details/81077226

* [Spring Cloud 系列文章](http://www.ityouknow.com/spring-cloud.html)
https://blog.csdn.net/ITTechnologyHome/article/details/73824784

Feign
https://www.jianshu.com/p/3d597e9d2d67
https://www.jianshu.com/p/191d45210d16
