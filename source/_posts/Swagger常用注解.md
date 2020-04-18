title: Swagger常用注解
author: LanGaoBai
author_id: defaultAuthorId
language: zh-CN
tags:
  - Swagger
  - API
categories:
  - API
  - Swagger
date: 2020-02-24 09:24:00

---

### 简介

swagger2可以将项目的所有接口在一个UI界面上展示出来。

同时表明了这个接口的用途：

接口需要的参数是什么类型参数是否必须，输入了参数可以直接测试接口类似postman的功能，会显示接口请求的状态码和返回的数据结构。

### 常用注解

#### 概览

| Name                                                         | Description                                  |
| ------------------------------------------------------------ | -------------------------------------------- |
| [@Api](https://github.com/swagger-api/swagger-core/wiki/Annotations#api) | 将一个类标记为Swagger资源。                  |
| [@ApiImplicitParam](https://github.com/swagger-api/swagger-core/wiki/Annotations#apiimplicitparam-apiimplicitparams) | 表示API操作中的单个参数。                    |
| [@ApiImplicitParams](https://github.com/swagger-api/swagger-core/wiki/Annotations#apiimplicitparam-apiimplicitparams) | 包装器，允许多个ApiImplicitParam对象的列表。 |
| [@ApiModel](https://github.com/swagger-api/swagger-core/wiki/Annotations#apimodel) | 提供有关Swagger模型的其他信息。              |
| [@ApiModelProperty](https://github.com/swagger-api/swagger-core/wiki/Annotations#apimodelproperty) | 添加和操作模型属性的数据。                   |
| [@ApiOperation](https://github.com/swagger-api/swagger-core/wiki/Annotations#apioperation) | 描述针对特定路径的操作或通常为HTTP方法。     |
| [@ApiParam](https://github.com/swagger-api/swagger-core/wiki/Annotations#apiparam) | 为操作参数添加其他元数据。                   |
| [@ApiResponse](https://github.com/swagger-api/swagger-core/wiki/Annotations#apiresponses-apiresponse) | 描述操作的可能响应。                         |
| [@ApiResponses](https://github.com/swagger-api/swagger-core/wiki/Annotations#apiresponses-apiresponse) | 包装器，允许多个ApiResponse对象的列表。      |
| [@Authorization](https://github.com/swagger-api/swagger-core/wiki/Annotations#authorization-authorizationscope) | 声明要在资源或操作上使用的授权方案。         |
| [@AuthorizationScope](https://github.com/swagger-api/swagger-core/wiki/Annotations#authorization-authorizationscope) | 描述OAuth2授权范围。                         |
| [@ResponseHeader](https://github.com/swagger-api/swagger-core/wiki/Annotations-1.5.X#responseHeader) | 表示可以作为响应的一部分提供的标头。         |

最新版本还添加了许多注释，用于在Swagger定义级别添加扩展和元数据：

| 名称                                                         | 描述                                    |
| ------------------------------------------------------------ | --------------------------------------- |
| [@SwaggerDefinition](https://github.com/swagger-api/swagger-core/wiki/Annotations-1.5.X#swaggerdefinition) | 要添加到生成的Swagger定义的定义级别属性 |
| [@Info](https://github.com/swagger-api/swagger-core/wiki/Annotations-1.5.X#info) | Swagger定义的常规元数据                 |
| [@Contact](https://github.com/swagger-api/swagger-core/wiki/Annotations-1.5.X#contact) | 描述Swagger定义联系人的属性             |
| [@License](https://github.com/swagger-api/swagger-core/wiki/Annotations-1.5.X#license) | 描述Swagger定义的许可证的属性           |
| [@Extension](https://github.com/swagger-api/swagger-core/wiki/Annotations-1.5.X#extension) | 添加具有包含属性的扩展                  |
| [@ExtensionProperty](https://github.com/swagger-api/swagger-core/wiki/Annotations-1.5.X#extensionproperty) | 将自定义属性添加到扩展                  |



#### 资源API声明

@API

在Swagger 2.0中，资源已被标签替换，这会影响`@Api`注释。它不再用于声明资源，现在用于为其下定义的所有操作应用定义。

JAX-RS的用法是：

```java

```

