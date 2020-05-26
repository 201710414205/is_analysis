
# 接口：selection_student  [返回](../README.md)
用例： [选课_学生](../用例/选课_学生.md)

- 功能：
    用于学生选择上课的课程。
    
- 权限：
    只有学生可以调用该API。
    
- API请求地址： 
    接口基本地址/v1/api/selection_student

- 请求方式 ：
    POST

- 请求实例：

        {
            "access_token": $access_token,
            "lesson_id": 1,
            "teacher_name": 赵卫东
        }

- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|
  |access_token|用于验证请求合法性的认证信息|
  |lesson_id|课程的id|
  |teacher_name|授课老师的姓名|
  
    
- 返回实例：

        {         
           "info": "选课成功",
            "status": true,
            "code": 200
        }
 
- 返回参数说明：    
 
  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |info|返回结果说明信息|
  |status|bool类型，true表示正确的返回，false表示有错误|
  |code|返回码|

