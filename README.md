[TOC]

# 声明
> 项目clone来自 [**李鹏军 / 微同商城**](https://gitee.com/fuyang_lipengjun/platform)


# 代码结构

项目结构也比较清晰，功能明确

![WX20190116-211745@2x.png](https://i.loli.net/2019/01/17/5c3fdee1a4d35.png)





# 项目架构



## 1.项目架构图

![商城架构.png](https://i.loli.net/2019/01/17/5c401c86da753.png)



##  2.项目功能点列举

* 会员管理：
  - 会员管理，会员等级，收货地址管理，会员优惠劵，会员收藏，会员足迹，搜索历史，购物车；

* 商城配置
  - 区域配置， 商品属性种类，品牌制造商，商品规格，订单管理，商品类型，渠道管理，商品问答，反馈，关键词；

* 商品编辑
  - 所有商品，用户评论，产品设置，商品规格，商品回收站；
* 推广管理
  * 广告列表， 广告位置，优惠劵管理， 专题管理，专题分类；
  
* 订单管理
  * 订单管理


* 系统管理
  * 管理员列表， 角色管理，菜单管理，SQL监控，定时任务，参数管理，代码生成器，系统管理，文件上传，通用词典；


* 消息管理
  * 短信验证码，短信通知，短信营销





# 技术选型

## 后端技术栈

| 序号 |       组件      |      版本      |                        项目地址                       |                                                                       备注                                                                       |
|:----:|:---------------:|:--------------:|:-----------------------------------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------:|
|   1  | springframework |  4.3.7.RELEASE |                                                       |                                                                                                                                                  |
|   2  |     mybatis     |      3.4.1     |         [mybatis](https://github.com/mybatis/)        |                                                 持久层框架，支持定制化 SQL、存储过程以及高级映射                                                 |
|   3  |      shiro      |      1.3.2     |        [shiro](https://github.com/apache/shiro)       | Apache Shiro 是一个强大易用的 Java  安全框架，提供了认证、授权、加密和会话 管理等功能，对于任何一个应用程序，Shiro  都可以提供全面的安全管理服务 |
|   4  |     servlet     |      3.1.0     |                                                       |                                                                                                                                                  |
|   5  |      druid      |     1.0.28     |       [druid](https://github.com/alibaba/druid)       |                                         阿里巴巴开源的， JDBC组件库，包括数据库连接池、SQL Parser等组件;                                         |
|   6  |      slf4j      |     1.7.19     |                 https://www.slf4j.org/                |                                                                     日志组件                                                                     |
|   7  |     fastjson    |     1.2.30     |    [fastjson](https://github.com/alibaba/fastjson)    |                                                             阿里巴巴开源的Json解析库                                                             |
|   8  |       poi       |      3.15      |          [poi](https://github.com/apache/poi)         |                                                        提供对Microsoft 文件操作的包工具；                                                        |
|   9  |     velocity    |       1.7      | [velocity](https://github.com/apache/velocity-engine) |                                                         Java模板库，模板引擎快速生成代码                                                         |
|  10  |      quartz     |      2.2.3     |  [quartz](https://github.com/quartz-scheduler/quartz) |                                                                    任务调度库                                                                    |
|  11  |      mysql      |     5.1.39     |                                                       |                                                                   关系型数据库                                                                   |
|  12  |     swagger     |       2.4      |                  https://swagger.io/                  |                                                                Rest API的描述语言                                                                |
|  13  |     j2cache     | 2.3.22-release |     [j2cache](https://github.com/oschina/J2Cache)     |                                                                   两级缓存框架                                                                   |
|  14  |  weixin-java-mp |      3.2.0     |                                                       |                                                                                                                                                  |



## 前端技术栈

- 2.1 Vue2.5.1
- 2.2 iview
- 2.3 layer3.0.3
- 2.4 jquery2.2.4
- 2.5 bootstrap3.3.7
- 2.6 jqgrid5.1.1
- 2.7 ztree3.5.26
- 2.8 froala_editor1.2.2



# 项目部署

## 1.环境依赖

* jdk1.8
* maven3.3
* tomcat8
* mysql5.7
* redis4.0.1
## 2.准备工作

1.数据库创建和表创建

```
source  绝对路径/*.sql
```

2. 导入证书(本地体验，可以省略)
导入支付证书至/platform-shop/src/main/resources/cert/目录下（申请商户号、开通微信支付、下载支付证书）

3. 修改配置文件
文件1： `/platform-admin/src/main/resources/dev/platform.properties`

- jdbc.url
- jdbc.username
- jdbc.password
- wx.appId
- wx.secret
- wx.mchId
- wx.paySignKey
- wx.notifyUrl
- sms.validIp
- mp.appId
- mp.secret
- mp.token
- mp.aesKey

文件2： ` /platform-admin/src/main/resources/j2cache.properties`

- redis.hosts
- redis.password



## 3.项目部署

### 3.1项目打包

```
 mvn clean install -Pdev -DskipTests 
```

### 3.2 拷贝 `war`包到tomcat

`/platform/platform-framework/target/platform.war` 到 `apache-tomcat-8.5.37/webapps`;

### 3.3 重启tomcat
### 3.4 访问

* 用户名：admin
* 密码: admin

```
http://localhost:8080/platform
```
![WX20190117-153704@2x.png](https://i.loli.net/2019/01/17/5c4030b8cb98a.png)


## 4.小程序代码运行

* 修改小程序项目`wx-mall`中的 `appid` 为自己的`appid`

  文件路径 `platform/wx-mall/project.config.json`

* 导入`小程序开发工具中`

![WX20190117-154024@2x.png](https://i.loli.net/2019/01/17/5c40317c6e3ab.png)




# 参考
1.[Dockerfile 最佳实践](https://yeasy.gitbooks.io/docker_practice/appendix/best_practices.html)
2.[redis 配置](1.https://zhuanlan.zhihu.com/p/43654441)
3.[shiro 入门](https://segmentfault.com/a/1190000013875092)

4.[Servlet 到 Spring MVC 的简化之路](https://juejin.im/post/5a9f3ddb5188255585071151)

