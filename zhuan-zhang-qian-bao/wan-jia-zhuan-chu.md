---
icon: coin-blank
---

# 玩家转出

#### 玩家转出 <a href="#h3--v1" id="h3--v1"></a>

**1) 请求地址**

> URL: {APIURL}/api/v1/player/transferOut

**2) 请求参数:**

| 参数名     | 类型            | 必填 | 描述         |
| ------- | ------------- | -- | ---------- |
| userid  | string\[4-40] | 是  | 运营商的玩家唯一标识 |
| amount  | float         | 是  | 转出金额 >0    |
| traceid | string\[4-40] | 是  | 交易单号       |

*   示例：

    ```json
    {
        "userid": "string",
        "amount": 10,
        "traceid": "string"
    }
    ```

请求示例代码:

```bash
curl --location --request POST 'https://{APIURL}/api/v1/player/transferOut' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "userid": "string",
    "amount": 10,
    "traceid": "string"
}'
```

**3) 返回结果:**

| 参数名            | 类型    | 描述      |
| -------------- | ----- | ------- |
| after\_balance | float | 转出成功后余额 |

* 正常返回
*   示例：

    ```json
    {
        "code": 0,
        "error": "",
        "data": {
            "after_balance": 492.8
        }
    }
    ```
* 订单号重复
*   示例：

    ```json
    {
    "code": 1,
    "error": "Order already exists",
    "data": null
    }
    ```
* 余额不足
*   示例：

    ```json
    {
    "code": 1,
    "error": "Insufficient wallet balance",
    "data": null
    }
    ```
