
# 接口：getStudentsByStudent [返回](../README.md)
用例： [查看成绩_学生](../用例/查看成绩_学生.md)

- 权限：
    学生：可以看到RESULT_SUM，WEB_SUM。

- 功能：
    返回所有自己的实验成绩列表。

- API请求地址：
   接口基本地址/v1/api/getStudentsByStudent

- 请求方式 ：
    GET

- 请求参数说明:
    无

- 返回实例：

        {
            "status": true,
            "info": null,
            "data": [
                {"WEB_SUM": "Y,Y,Y,Y,Y,N",
                "RESULT_SUM": "83.75,90,80,80,85,N",
                "GITHUB_USERNAME": "Chinajuedui",
                "STUDENT_ID": "201510315203",
                "CLASS": "软件(本)17-1",
                "NAME": "张三",
                "UPDATE_DATE": "2020-04-02 13:48:01"},
                {
                ...其他课程
                }
            ]
        }

- 返回参数说明：

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|
  |data|学生实验成绩的数组|
  |WEB_SUM|网址是否正确的汇总|
  |RESULT_SUM|成绩的汇总|
  |GITHUB_USERNAME|GITHUB 用户名|
  |STUDENT_ID|学号|
  |CLASS|班级|
  |NAME|真实姓名|
  |UPDATE_DATE|GitHUB用户名修改日期|