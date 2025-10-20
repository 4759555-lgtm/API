---
icon: coin
---

# 玩家转入

#### 玩家转入 <a href="#wan-jia-zhuan-ru-v1" id="wan-jia-zhuan-ru-v1"></a>

**1) 请求地址**

> URL: {APIURL}/api/v1/player/transferIn

**2) 请求参数:**

| 参数名     | 类型            | 必填 | 描述           |
| ------- | ------------- | -- | ------------ |
| userid  | string\[4-40] | 是  | 运营商的玩家唯一标识   |
| amount  | float         | 是  | 转入金额 >0，最大1亿 |
| traceid | string\[4-40] | 是  | 交易单号         |

*   示例：

    ```json
    {
        "userid": "string",
        "amount": 10,
        "traceid": "string"
    }
    ```

请求示例代码：

```bash
curl --location --request POST 'https://{APIURL}/api/v1/player/transferIn' \
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

| 参数名                 | 类型      | 描述            |
| ------------------- | ------- | ------------- |
| code                | integer | 返回状态码，0 表示成功  |
| error               | string  | 错误信息，成功时为空字符串 |
| data                | object  | 返回数据          |
| data.after\_balance | float   | 充值成功后余额       |

* 正常返回
*   示例：

    ```json
    {
        "code": 0,
        "error": "",
        "data": {
            "after_balance": 493.8
        }
    }
    ```
* 订单重复
*   示例：

    ```json
    {
    "code": 1,
    "error": "Order already exists",
    "data": null
    }
    ```
