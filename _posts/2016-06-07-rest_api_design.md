---
layout: post
title: REST Web API 设计
date: 2016-06-07 16:21:34 +0800
tags: [REST, Design]
---

REST Web API 设计

---
1. 为何使用REST风格设计Web API？
  REST 风格的API层次清晰，方便分类和调用，尤其是项目规模越来越大时。

2. REST API应遵循什么原则？
  REST的定义参见：http://www.ruanyifeng.com/blog/2011/09/restful.html （理解RESTful架构 － 阮一峰）
  基本设计原则：
  * URL表达特定的资源，因此应该用名词描述，不应该出现动词；
  * 使用HTTP请求方法（GET POST PUT DELETE）表达对资源的操作行为；
  * 名词根据需要可以使用层级嵌套；
  * URL终点名词采用复数形式；
  * 额外信息，比如一些查询参数、分页参数可以用?k=v&a=b的形式

3. 特定场景的处理

+ API的多版本
  可以将版本信息写入HTTP header中（比如x-version: 2.1）
  另外也可以加入到URL中。从实践来看，后者好些，github也是这么干的。

+ 依赖URL的权限系统设计
  权限设计中可能把URL＋HTTP METHOD作为权限主体，URL严格遵循层次结构可以缩减权限配置纪录的数目。


+ 资源层次关系较多
  使用别名或者省略一些层次以使URL短些，但慎用。

+ 资源的不同形式
  比如一个表单数据，可能的展现形式有：html、pdf、doc、image等；
  可以把这些信息通过http header表达（自定义x-media-type或者通过content-type指定）；
  也可以用URL表达，比如 order.html order.pdf order.doc ...


4. REST API设计案例？

+ github
  https://developer.github.com/v3/

5. 另外，参见HyperMedia API（在返回结果中提供链接指向其它API，以给用户提供便利）

----
参考资料：
http://www.ruanyifeng.com/blog/2014/05/restful_api.html RESTful API设计指南 －阮一峰
