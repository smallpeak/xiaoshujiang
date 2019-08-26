---
title: Sentinel调研
tags: QPS,限流
grammar_cjkRuby: true
---


# 1.Sentinel提供的能力
![主要的特性](https://user-images.githubusercontent.com/9434884/50505538-2c484880-0aaf-11e9-9ffc-cbaaef20be2b.png)


# 2.Hystrix提供的能力
![场景](https://raw.githubusercontent.com/wiki/Netflix/Hystrix/images/soa-2-640.png)


## Sentinel与Hystrix功能比较
[限流熔断技术选型：从Hystrix到Sentinel](https://www.sohu.com/a/282806665_268033)

|  	| Sentinel | 	Hystrix |  Resilience4j |
| -------- | ---------- | ------- | ------- |
| 隔离策略 | 信号量隔离 |	线程池隔离/信号量隔离  | 信号量隔离 |
| 熔断降级策略  | 	基于响应时间或失败比率 	基于失败比率  |  基于异常比率、响应时间 |
| 实时指标实现 |	滑动窗口 	滑动窗口（基于 RxJava）  | Ring Bit Buffer |
| 规则配置 	支持多种数据源  | 	支持多种数据源  | 有限支持 | 
| 扩展性  | 	多个扩展点  | 	插件的形式  | 接口的形式 |
| 基于注解的支持  | 	支持  | 	支持  |	支持  |
| 限流  | 	基于 QPS，支持基于调用关系的限流  | 	有限的支持  | Rate Limiter |
| 流量整形  | 	支持慢启动、匀速器模式  | 	不支持  | 简单的 Rate Limiter 模式 |
| 系统负载保护  | 	支持  | 	不支持  |  不支持 |
| 控制台  | 	开箱即用，可配置规则、查看秒级监控、机器发现等  | 	不完善  | 不提供控制台，可对接其它监控系统 |
| 常见框架的适配  | 	Servlet、Spring Cloud、Dubbo、gRPC 等  | 	Servlet、Spring Cloud Netflix  |
| 收欢迎程度 |      Star:8428 Fork:2442 2019/8/26最后一次代码体检   |       Star:18119 Fork:3729  2018/10/20最后一次代码体检     |  Star:4121 Fork:490 2019/8/26最后一次代码体检  |
| 开源公司 | 阿里  双11  | NetFlix  停止更新维护 |  缺乏生产级别的配套设施 |



 1. Hystrix关注点
      隔离 和 熔断 为主的容错机制，超时或被熔断的调用将会快速失败，并可以提供 fallback 机制
 2. Sentinel关注点
    多样化的流量控制
    熔断降级
    系统负载保护
    实时监控和控制台
 3. Resilience4j关注点
    Hystrix停更后的官方推荐方案
	轻量的熔断降级库
	使用较小较新的项目，缺乏生产级别的配套设施

