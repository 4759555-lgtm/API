---
icon: circle-sterling
---

# 获取玩家余额

#### 获取玩家余额 <a href="#huo-qu-wan-jia-yu-e" id="huo-qu-wan-jia-yu-e"></a>

**1) 请求地址:**

> URL: {OPURL}/Cash/Get

**2) 请求参数:**

| 参数名    | 类型     | 描述                |
| ------ | ------ | ----------------- |
| userid | string | 运营商的玩家唯一标识(需全局唯一) |

**示例请求:**

```json
{
  "userid": "testuser1"
}
```

**3) 返回结果:**

| 参数名          | 类型      | 描述                  |
| ------------ | ------- | ------------------- |
| code         | integer | 返回状态码，0 表示成功        |
| error        | string  | 错误信息，成功时为空字符串       |
| data         | object  | 返回数据                |
| data.balance | float   | 玩家当前可用余额, 此余额为运营商余额 |

**示例响应:**

```json
{
  "code": 0,
  "error": "",
  "data": {
    "balance": 10994.12
   }
}
```
