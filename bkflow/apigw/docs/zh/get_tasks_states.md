### 资源描述

批量获取任务状态

### 输入通用参数说明
| 参数名称          | 参数类型   | 必须 | 参数说明                                                       |
|---------------|--------|----|------------------------------------------------------------|
| bk_app_code   | string | 是  | 应用ID(app id)，可以通过 蓝鲸开发者中心 -> 应用基本设置 -> 基本信息 -> 鉴权信息 获取     |
| bk_app_secret | string | 是  | 安全秘钥(app secret)，可以通过 蓝鲸开发者中心 -> 应用基本设置 -> 基本信息 -> 鉴权信息 获取 |

#### 接口参数
| 字段       | 类型        | 必选 | 描述            |
|----------|-----------|----|---------------|
| task_ids | list[int] | 是  | 需要查询的任务 id 列表 |


### 请求参数示例
```json
{
    "bk_app_code": "xxxx",
    "bk_app_secret": "xxxx",
    "bk_username or bk_token": "xxxx",
    "task_ids": [1, 2, 3, 4]
}
```


### 返回结果示例

```json
{
    "result": true,
    "data": {
        "3": {
            "state": "FINISHED"
        },
        "2": {
            "state": "FINISHED"
        },
        "1": {
            "state": "FINISHED"
        }
    },
    "code": "0",
    "message": ""
}
```
### 返回结果参数说明

| 字段      | 类型     | 描述                    |
|---------|--------|-----------------------|
| result  | bool   | 返回结果，true为成功，false为失败 |
| code    | int    | 返回码，0表示成功，其他值表示失败     |
| message | string | 错误信息                  |
| data    | dict   | 返回数据                  |

#### data[item]

| 字段              | 类型     | 描述        |
|-----------------|--------|-----------|
| id              | string | 任务实例ID    |
| state           | string | 任务状态      |