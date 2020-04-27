# 实验5：图书管理系统数据库设计与界面设计

|     学号     |     班级     | 姓名 |
| :----------: | :----------: | :--: |
| 201710414205 | 软件(本)17-2 | 胡古 |

## 1.数据库表设计

## 1.1. 图书信息表

|    字段    |     类型     | 主键，外键 | 可以为空 | 默认值 | 约束 |
| :--------: | :----------: | :--------: | :------: | :----: | :--: |
|     ID     |    int(4)    |    主键    |    否    |        |      |
|    Name    | varchar(100) |            |    否    |        |      |
|   Price    |    int(4)    |            |    否    |        |      |
| borrowTime |   datetime   |    外键    |    是    |        |      |
| returnTime |   datetime   |    外键    |    是    |        |      |
| borrowName | varchar(50)  |            |    是    |        |      |
|            |              |            |          |        |      |

## 1.2. 用户信息表

|    字段    |    类型     | 主键，外键 | 可以为空 | 默认值 | 约束 |
| :--------: | :---------: | :--------: | :------: | :----: | :--: |
|     ID     |   int(4)    |    主键    |    否    |        |      |
|    Name    | varchar(50) |            |    否    |        |      |
| borrowBook | varchar(50) |    外键    |    是    |        |      |
|  password  | varchar(50) |            |    否    |        |      |
|  isReturn  |    bool     |            |    否    |        |      |

## 1.3. 学生借阅信息登记表

| 字段               | 类型        | 主键，外键 | 可以为空 | 默认值 | 约束 |
| ------------------ | ----------- | ---------- | -------- | ------ | ---- |
| save_id            | int(8)      | 主键       | 否       |        |      |
| book_id            | int(8)      | 外键       | 否       |        |      |
| read_id            | varchar(20) | 外键       | 否       |        |      |
| borrow_date        | datetime    |            | 否       |        |      |
| except_return_date | datetime    |            | 否       |        |      |
| return_date_count  | int(5)      |            | 是       |        |      |
| return_date        | datetime    |            | 是       |        |      |
| over_date          | int(100)    |            | 是       |        |      |
| ticket_fee         | float       |            | 是       |        |      |

***

## 2. 界面设计

## 2.1. 用户界面设计

[https://201710414205.github.io/is_analysis_pages/ui/首页.html](https://201710414205.github.io/is_analysis_pages/ui/首页.html)

- 用例图参见：登录用例
- 类图参见：用户类图
- 顺序图参见：用户顺序图
- API接口如下：

1. 获取全部分类

- 功能：用户登录
- 请求地址： http://bookSystem/api/login
- 请求方法：POST
- 请求参数：

| 参数名称 | 必填 |   说明   |
| :------: | :--: | :------: |
| userName |  是  | 用户账号 |
| password |  是  | 用户密码 |
|  method  |  是  |   GET    |

- 返回实例：

```
{
    "data": {
        "userName":"123456",
        "password": "123456",
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
- 请求地址：  [https://201710414205.github.io/is_analysis_pages/ui/个人信息修改.html](https://201710414205.github.io/is_analysis_pages/ui/个人信息修改.html)
- 请求方法：GET
- 请求参数：

|   参数名称   | 必填 |              说明              |
| :----------: | :--: | :----------------------------: |
| access_token |  是  | 用于验证请求合法性的认证信息。 |
|    method    |  是  |              POST              |
|     code     |  是  |             验证码             |
|     name     |  是  |            用户账号            |
|   password   |  是  |            用户密码            |

- 返回实例：

```
{
    "data": {
        "userName":"123456",
        "password": "123456",
        "code":"zc4s",
        "method":"POST"
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

## 2.2.书籍界面设计

- 用例图参见：书籍用例
- 类图参见：用户类，书籍类
- 顺序图参见：书籍借阅顺序图
- API接口如下：

1. 书籍预约

- 功能：查询、借阅书籍
- 请求地址：[https://201710414205.github.io/is_analysis_pages/ui/查询图书.html](https://201710414205.github.io/is_analysis_pages/ui/查询图书.html)
- 请求方法：GET
- 请求参数：

| 参数名称  | 必填 | 说明                           |
| --------- | ---- | ------------------------------ |
| rule_take | 是   | 用于验证请求合法性的认证信息。 |
| method    | 是   | GET                            |

- 返回实例：

```
{
    "info": "借阅书籍",
    "data": {
        "userId": "188289",
        "userName": "小明",
        "book_id": "001",
        "book_name": "亚索之路",
        "borrow_date": "2020.1.20",
        "except_return_date": "2020.2.20",
      }
       
    "code": 200
}
```

- 返回参数说明：

| 参数名称           | 说明             |
| ------------------ | ---------------- |
| Info               | 借阅书籍         |
| reader_id          | 读者id           |
| reader_name        | 读者名称         |
| book_id            | 书籍id           |
| book_name          | 书籍名称         |
| borrow_date        | 书籍借阅日期     |
| except_return_date | 预期书籍归还日期 |
| code               | 返回码           |

2.添加图书

- 功能：添加书籍
- 请求地址：[https://201710414205.github.io/is_analysis_pages/ui/新增图书.html](https://201710414205.github.io/is_analysis_pages/ui/新增图书.html)
- 请求方法：PUT
- 请求参数：

| 参数名称  | 必填 | 说明                           |
| --------- | ---- | ------------------------------ |
| rule_take | 是   | 用于验证请求合法性的认证信息。 |
| method    | 是   | PUT                            |

- 返回实例：

```
{
    "info": "借阅书籍",
    "data": {
        "userId": "188289",
        "userName": "小明",
        "book_id": "001",
        "book_name": "亚索之路",
      }
       
    "code": 200
}
```

- 返回参数说明：

| 参数名称 | 说明     |
| -------- | -------- |
| Info     | 借阅书籍 |
| bookId   | 图书ID   |
| price    | 图书价格 |
| num      | 图书数量 |
| code     | 返回码   |

3.逾期未还

- 功能：查看逾期未还信息
- 请求地址：[https://201710414205.github.io/is_analysis_pages/ui/逾期未还.html](https://201710414205.github.io/is_analysis_pages/ui/逾期未还.html)
- 请求方法：GET
- 请求参数：

| 参数名称  | 必填 | 说明                           |
| --------- | ---- | ------------------------------ |
| rule_take | 是   | 用于验证请求合法性的认证信息。 |
| method    | 是   | GET                            |

- 返回实例：

```
{
    "info": "查询逾期未还",
    "data": {
        "userId": "003",
        "book_id": "001",
        "book_name": "亚索之路",
        "borrowTime":"2019-11-11",
        "punish":"8"
      }
       
    "code": 200
}
```

- 返回参数说明：

| 参数名称   | 说明         |
| ---------- | ------------ |
| Info       | 查询逾期未还 |
| bookId     | 图书ID       |
| bookName   | 图书名字     |
| punish     | 罚款数量     |
| code       | 返回码       |
| borrowTime | 应该归还日期 |