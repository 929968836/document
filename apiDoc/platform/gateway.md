##  网关仿真接口  

**功能说明**  
开发阶段启动后，通过对后台服务接口设置默认值，以供web前端、app调用，方便前端开发，使前后端可以并行开发，提高开发效率。
**该功能仅面向后台接口的开发人员。**

---
##  1.设置接口默认值  ##

 **version** 1.0

**1.功能说明**
	
设置接口默认值，有效期暂定为一周  

**2. 调用接口说明**

**2.1	请求路径**  
    网关域名/mockappend  

**2.2	HTTP请求方式**  
POST
      
**2.3	格式**  
json

**2.4	输入参数说明**

|参数名称|是否必须|类型|字段描述|备注|
|-----|-----|-----|-----|---|---|
|key|Y|string|api接口的网关访问路径||
|value|Y|string|默认值|||
|sgin|Y|string|签名|46ccdc59-c4f1-11e7-aa97-005056842f6c(仅用于开发环境)|

**注意**  
**key：**是api接口的网关访问路径，不仅仅是api接口的路径。  
api接口的网关访问路径是，服务的网关路由名+api接口路径。  
如：/user/usercenter/black/get  
**/user**对应的是网关路由的服务名，具体服务名请参照 <a href="微服务配置清单.md">微服务配置清单</a>中的**网关访问路径**。  
**/usercenter/black/get**对应就是api接口本身的访问路径，即**@RequestMapping的value值**。  

**value：**新架构的接口返回值统一使用**ResultObject**，所以value值的结构是**ResultObject的json字符串**，比如："{\"code\":1,\"msg\":\"成功\",\"data\":{\"field\":\"value\"}}"。
      
**2.5 入参示例**	 

json示例：
	
    {
      "key":"/user/usercenter/black/get",
      "value":"{\"code\":1,\"msg\":\"成功\",\"data\":{\"field\":\"value\"}}",
      "sign":"46ccdc59-c4f1-11e7-aa97-005056842f6c"
    }
    
**2.6 返回示例**	 

json示例：
	
    {
        "code": 1,
        "msg": "添加成功!",
        "data": true
    }

##  2.删除接口默认值  ##

 **version** 1.0

**1.功能说明**
	
删除接口默认值，当相应接口开发完成之后，需删除对应的默认值  

**2. 调用接口说明**

**2.1	请求路径**  
    网关域名/mockdel  

**2.2	HTTP请求方式**  
DELETE
      
**2.3	格式**  
json

**2.4	输入参数说明**

|参数名称|是否必须|类型|字段描述|备注|
|-----|-----|-----|-----|---|---|
|key|Y|string|api接口的网关访问路径||
|sgin|Y|string|签名|46ccdc59-c4f1-11e7-aa97-005056842f6c(仅用于开发环境)|

**注意**  
**key：**是api接口的网关访问路径，不仅仅是api接口的路径。  
api接口的网关访问路径是，服务的网关路由名+api接口路径。  
如：/user/usercenter/black/get  
**/user**对应的是网关路由的服务名，具体服务名请参照 <a href="微服务配置清单.md">微服务配置清单</a>中的**网关访问路径**。  
**/usercenter/black/get**对应就是api接口本身的访问路径，即**@RequestMapping的value值**。  

**value：**新架构的接口返回值统一使用**ResultObject**，所以value值的结构是**ResultObject的json字符串**，比如："{\"code\":1,\"msg\":\"成功\",\"data\":{\"field\":\"value\"}}"。
      
**2.5 入参示例**	 

json示例：
	
    {
      "key":"/user/usercenter/black/get",
      "sign":"46ccdc59-c4f1-11e7-aa97-005056842f6c"
    }
    
**2.6 返回示例**	 

json示例：
	
    {
        "code": 1,
        "msg": "删除成功!",
        "data": true
    }

##  3.查询接口默认值  ##

 **version** 1.0

**1.功能说明**
	
查询接口默认值，用于查询api接口是否已经设置了默认值  

**2. 调用接口说明**

**2.1	请求路径**  
    网关域名/mockget  

**2.2 HTTP请求方式**  
GET
      
**2.3 格式**


**2.4 输入参数说明**

|参数名称|是否必须|类型|字段描述|备注|
|-----|-----|-----|-----|---|---|
|key|Y|string|api接口的网关访问路径||

**注意**  
**key：**是api接口的网关访问路径，不仅仅是api接口的路径。  
api接口的网关访问路径是，服务的网关路由名+api接口路径。  
如：/user/usercenter/black/get  
**/user**对应的是网关路由的服务名，具体服务名请参照 <a href="微服务配置清单.md">微服务配置清单</a>中的**网关访问路径**。  
**/usercenter/black/get**对应就是api接口本身的访问路径，即**@RequestMapping的value值**。  

**2.5 访问示例**  

示例：
	
    http://192.168.113.15:18746/mockget?key=/user/usercenter/black/get 
    
**2.6 返回示例**	 

json示例：  
**有值**：  
	
    {
        "code": 1,
        "msg": "成功",
        "data": "{\"code\":111,\"msg\":\"hahaha\",\"data\":{\"hi\":\"hello\"}}"
    }
	
**没有值**：  

    {
        "code": 1,
        "msg": "成功!",
        "data": ""
    }
---


@author: pengchao

@date:2017/11/10