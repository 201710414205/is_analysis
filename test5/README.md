# 实验5：图书管理系统数据库设计与界面设计
|     学号     |     班级     | 姓名 |
| :----------: | :----------: | :--: |
| 201710414205 | 软件(本)17-2 | 胡古 |

## 1.数据库表设计

## 1.1. 图书表
|    字段    |     类型     | 主键，外键 | 可以为空 | 默认值 | 约束 |
| :--------: | :----------: | :--------: | :------: | :----: | :--: |
|     ID     |    int(4)    |    主键    |    否    |        |      |
|    Name    | varchar(100) |            |    否    |        |      |
|   Price    |    int(4)    |            |    否    |        |      |
| borrowTime |   datetime   |            |    是    |        |      |
| returnTime |   datetime   |            |    是    |        |      |
| borrowName | varchar(50)  |            |    是    |        |      |
|            |              |            |          |        |      |

## 1.2. 用户表
|    字段    |    类型     | 主键，外键 | 可以为空 | 默认值 | 约束 |
| :--------: | :---------: | :--------: | :------: | :----: | :--: |
|     ID     |   int(4)    |    主键    |    否    |        |      |
|    Name    | varchar(50) |            |    否    |        |      |
| borrowBook | varchar(50) |            |    是    |        |      |
|  password  | varchar(50) |            |    否    |        |      |
|  isReturn  |    bool     |            |    否    |        |      |

***

## 2. 界面设计
## 2.1. 借书界面设计
![pic1](pic1.png)
- 用例图参见：借书用例
- 类图参见：借书类，读者类
- 顺序图参见：借书顺序图
- API接口如下：

1. 获取全部分类

- 功能：用于获取全部分类
- 请求地址： http://[YOUR_DOMAIN]/api/authorization
- 请求方法：POST
- 请求参数：

|   参数名称   | 必填 |              说明              |
| :----------: | :--: | :----------------------------: |
|      id      |  是  |         放在接口<id>处         |
| access_token |  是  | 用于验证请求合法性的认证信息。 |
|    method    |  是  |       GET（注意必须大写)       |

- 返回实例：
```
{
    "data": {
        "borrowNumber": "1",
        "ReadID": "001",
        "BookID": "201",
        "borrowTime": "2020-11-03",
        "returnTime": "2020-12-12",
        "avatar128": "http://upload.opensns.cn/Uploads_Avatar_14361_58e4b58fccf81.jpg?imageMogr2/crop/!260x260a6a22/thumbnail/128x128!",
        "avatar512": "http://upload.opensns.cn/Uploads_Avatar_14361_58e4b58fccf81.jpg?imageMogr2/crop/!260x260a6a22/thumbnail/512x512!"
    },
    "code": 200
}
```
- 返回参数说明：
  
| 参数名称 |      说明      |
| :------: | :------------: |
|   Info   |    返回信息    |
|   data   | 用户的个人信息 |
|   dodo   |     返回码     |

2. 修改用户基本信息API
- 功能：修改用户基本信息
- 请求地址： http://[YOUR_DOMAIN]/api/use
- 请求方法：GET
- 请求参数：

|   参数名称   | 必填 |                   说明                   |
| :----------: | :--: | :--------------------------------------: |
| access_token |  是  |      用于验证请求合法性的认证信息。      |
|    method    |  是  |          PUT（注意必须大写）。           |
|   open_id    |  是  | 用户登录凭证，flag参数为my和follow时必填 |
|     name     |  是  |                 用户账号                 |
|   password   |  是  |                 用户密码                 |

- 返回实例：
```
{
    "data": {
        "borrowNumber": "1",
        "ReadID": "001",
        "BookID": "201",
        "borrowTime": "2020-11-03",
        "returnTime": "2020-12-12",
        "avatar128": "http://upload.opensns.cn/Uploads_Avatar_14361_58e4b58fccf81.jpg?imageMogr2/crop/!260x260a6a22/thumbnail/128x128!",
        "avatar512": "http://upload.opensns.cn/Uploads_Avatar_14361_58e4b58fccf81.jpg?imageMogr2/crop/!260x260a6a22/thumbnail/512x512!"
    },
    "code": 200
}
```
- 返回参数说明：
  
| 参数名称 |      说明      |
| :------: | :------------: |
|   Info   |    返回信息    |
|   data   | 用户的个人信息 |
|   code   |     返回码     |


