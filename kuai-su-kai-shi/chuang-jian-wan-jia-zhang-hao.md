---
icon: user-shakespeare
---

# 创建玩家帐号

#### 创建玩家帐号 <a href="#h3-u521bu5efau73a9u5bb6u5e10u53f7" id="h3-u521bu5efau73a9u5bb6u5e10u53f7"></a>

**1) 请求地址**

> URL: {APIURL}/api/v1/player/create

**2）请求参数:**

| 参数名      | 类型            | 描述                                        |
| -------- | ------------- | ----------------------------------------- |
| userid   | string\[4-40] | 运营商的玩家唯一标识（注意不能填特殊字符，例如”。建议仅使用数字，英文，下划线。） |
| username | string\[4-40] | 玩家昵称（可选）                                  |

*   示例：

    ```json
    {
        "userid": "abc22",
        "username": "abc22"
    }
    ```

请求示例代码：

```powershell
curl --location --request POST 'https://hpgamecenter.pg-nmx.com/api/v1/player/create' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "userid": "string",
    "username": "string"
}'
```

**3) 返回结果:**

| 参数名 | 类型    | 描述       |
| --- | ----- | -------- |
| pid | int64 | 平台玩家唯一标识 |

*   示例：

    ```json
    {
    "error": "",
    "data": {
      "pid": 100064
     }
    }
    ```
* 重复创建同一个玩家, 返回相同的结果
* /api/v1/player/transferIn 和 /api/v1/game/launch 会自动创建玩家

