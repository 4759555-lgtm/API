---
icon: coin-front
---

# 玩家转出所有余额

#### 玩家转出所有余额 <a href="#h3--v1" id="h3--v1"></a>

**1) 请求地址**

> URL: {APIURL}/api/v1/player/transferOutAll

**2) 请求参数:**

| 参数名     | 类型            | 描述         |
| ------- | ------------- | ---------- |
| userid  | string\[4-40] | 运营商的玩家唯一标识 |
| traceid | string\[4-40] | 交易单号       |

*   示例：

    ```json
    {
    "userid": "user_id",
    "traceid": "fdsafaagg1234"
    }
    ```

**请求示例代码**

```powershell
curl --location --request POST 'https://hpgamecenter.pg-nmx.com/api/v1/player/transferOutAll' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "userid": "string",
    "traceid": "string"
}'
```

**3) 返回结果:**

| 参数名    | 类型    | 描述     |
| ------ | ----- | ------ |
| amount | float | 共转出的总额 |

*   示例：

    ```json
    {
    "code": 0,
    "error": "",
    "data": {
      "amount": 123.45
     }
    }
    ```
