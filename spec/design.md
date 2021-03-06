# 设计

## 原则
1. 开放封闭原则（Open Closed Principle）
1. 约定大于配置（惯例优先原则）

## 架构
1. 系统架构（船架）
1. 业务隔离机制（船的防水隔离）
1. 系统profile（体检）

## 操作
1. 除了数据库连接，其他配置都存在数据库
1. 所有操作都要有反馈。特别是API，一定要有返回码。
1. 所有机密页面（资金，订单等），当前用户必须是机密拥有人。
1. 所有重要/资金业务(注册，下单，退款，发货等)在数据改变时都必须log业务结果(成功info，失败error)。
1. 默认日期按照从大到小排序
1. 使用分布式锁确保数据一致
    1. 锁定内的运行时间越短越好(只锁定小段代码或者MQ执行)，因为锁定默认超时时间是5秒，其他锁如果超过时间会抛出异常。一个业务的不同代码片段可以分部用不同的资源来锁定。支持一个线程内多次锁定同一个资源，即可以嵌套锁。
    1. 锁定的是业务(service)，不是数据调整(dao和CRUD)。一个业务对应多个数据调整，锁在业务上，而不是每个数据调整都锁定。
    1. 锁定的是一套业务，而不是每个业务独立。锁定的资源数量等于调试的表数量。如优惠券领取业务，有两个接口(1. 领券，2. 用户是否已领券)。1的资源有券(保护券数量)和用户优惠券(保护用户的最大领券数量)，2的资源有用户优惠券。
```java
Order o = getOrder(id);
if (o is unpay) { // 提高性能的判断，只适用于单向状态图
    try (Lock lock = lock(getLockName("Order", id))) {
        o = getOrder(id);
        if (o is unpay)
            payOrder(id);
    }
}
```
