# SpringBoot

* [关闭](http://tech.dianwoda.com/2017/12/18/chang-jian-javaying-yong-you-ya-guan-bi/)

## Security
[SpringBoot配置属性之Security](https://segmentfault.com/a/1190000004309242)

## MQ
[SpringBoot配置属性之MQ](https://segmentfault.com/a/1190000004309900)

## Actuator
[SpringBoot四大神器之Actuator](https://segmentfault.com/a/1190000004318360)

## 启动
--spring.profiles.active=prod --spring.config.location=./application.yml

## 配置
* [配置参数](https://docs.spring.io/spring-boot/docs/current/reference/html/common-application-properties.html)
* [多环境配置](https://docs.spring.io/spring-boot/docs/current/reference/html/howto-properties-and-configuration.html)

```
---
spring:
	profiles: development
server:
	port: 9001

---
spring:
	profiles: production
server:
	port: 9002
```
