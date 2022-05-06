# API编写规范

* [API规范](https://tech.wangyaqi.cn/#/common/api)

## 说明
1. 使用swagger编写
1. 正式环境不开放
1. 网址：http://site/swagger-ui.html

## 使用
* 函数定义

@ApiOperation(value = "名称", tags = { "所属模块" }, notes = "说明") // 比如模块有系統，账户，商城等

* 参数定义

可选项：required，dataType

@ApiImplicitParam(name = "json", value = "{\"ex\":false}。参数说明：ex(是否异常)", required = true, dataType = "string")

* 返回定义
```
@ApiResponse(code = 200, message = "{\"id\":1000}。参数说明：id(订单号)") // 成功返回
@ApiResponse(code = 500, message = "101,1000") // 错误返回，所有的特定业务返回码
```

## 参考
* [json工具](http://www.jsoneditoronline.org/)
* [Swagger注解说明](https://github.com/swagger-api/swagger-core/wiki/annotations)
* [swagger 自动生成Api文档](https://qiyatech.gitbooks.io/techdocs/content/kai-fa-ji-cheng-an-zhuang/swagger-zi-dong-sheng-cheng-api-wen-dang.html)
