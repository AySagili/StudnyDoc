# 软件测试
## 软件测试云实训平台
### 接口文档
模块:登录

url:http://192.168.46.3:32102/prod-api/auth/login

method：POST

请求体参数:
~~~json
{
    "username": string,
    "password": string,
    "code": string,
    "uuid": string,
    "roleId": string
}
~~~

请求样例:
~~~json
{
    "username": "admin",
    "password": "admin123",
    "code": "17",
    "uuid": "fd1ea3eea2e74891a54492c2b5c0ac78",
    "roleId": "1"
}
~~~

返回参数:


成功
~~~json
{
    "code": int,
    "msg"?: string,
    "data"?: object
}
~~~

失败
~~~json
{
    "code": int,
    "msg"?: string,
    "data"?: object
}
~~~
返回参数案例:
~~~json
{
    "code": 200,
    "msg": null,
    "data": {
        "access_token": "d9a37f64-0092-463f-a43d-b31aed3f23f9",
        "name": "管理员",
        "photo": "",
        "expires_in": 43200
    }
}
~~~
模块:用户管理

url:http://192.168.46.3:32102/prod-api/system/user

添加角色

method:POST

请求参数
~~~json
{
    "majorIds": [object]
    "userName": string,
    "name": string,
    "password": string,
    "status": string,
    "roleId": int
}
~~~
请求参数案例
~~~json
{
    "majorIds": [
        {
            "majorid": "",
            "clazzIds": [
                "1"
            ],
            "majorId": "1",
            "sysClazzes": [
                {
                    "clazzId": "1"
                }
            ]
        }
    ],
    "userName": "test",
    "name": "test",
    "password": "123456",
    "status": "0",
    "roleId": 3
}
~~~
软件配置
| 测试类型 | 测试环境及工具 |
|:--------:|:--------------:|
|    1     |       2        |
|    1     |       2        |


硬件配置
| 设备项 | 数量 | 配置 |
|:------:|:----:|:----:|
| 客户端 |  1   |  1   |
| 移动端 |  1   |  1   |

人力资源分配
<div style="text-align: center;">
<table style="margin: 0 auto;">
  <tr>
    <th>人员<br>(工位号)</th>
    <th>角色</th>
    <th>主要职责</th>
    <th>产出</th>
  </tr>
  <tr>
    <td>1</td>
    <td>张三</td>
    <td>90</td>
    <td rowspan="2">优秀</td>
  </tr>
  <tr>
    <td>3</td>
    <td>王五</td>
    <td>85</td>
  </tr>
</table>
</div>
硬件配置
|   属性   | 内容                               |
|:------:|----------------------------------|
| 测试目标 | 验证系统的性能                     |
| 测试范围 | 所有核心功能模块                   |
| 应用技术 | 自动化测试工具（如 Selenium）        |
| 执行步骤 | 1. 准备测试环境<br>2. 执行测试用例 |
| 开始标准 | 测试环境准备完毕                   |
| 完成标准 | 所有测试用例执行完毕并通过         |


