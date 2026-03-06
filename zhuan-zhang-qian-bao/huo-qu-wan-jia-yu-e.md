---
icon: sack-dollar
---

# 获取玩家余额

#### 获取玩家余额 <a href="#h3-u83b7u53d6u73a9u5bb6u4f59u989d" id="h3-u83b7u53d6u73a9u5bb6u4f59u989d"></a>

**1) 请求地址**

> URL: {APIURL}/api/v1/player/balance

**2) 请求参数:**

| 参数名     | 类型             | 必填 | 描述                                                          |
| ------- | -------------- | -- | ----------------------------------------------------------- |
| userids | array\[string] | 是  | 运营商的玩家ID，单次查询最多<mark style="color:red;">**1000**</mark>个玩家。 |

*   示例：

    ```json
    {
        "userids": [
            "jNfyOjhF-1757301369938-DemoUser",
            "trZXIUZt-1757388232303-DemoUser"
        ]
    }
    ```

**请求示例代码**

```bash
curl --location --request POST 'https://{APIURL}/api/v1/player/balance' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "userids": [
        "jNfyOjhF-1757301369938-DemoUser",
        "trZXIUZt-1757388232303-DemoUser"
    ]
}'
```

**3) 返回结果:**

| 参数名                  | 类型             | 描述              |
| -------------------- | -------------- | --------------- |
| code                 | integer        | 返回状态码，0 表示成功    |
| error                | string         | 错误信息，成功时为空字符串   |
| data                 | object         | 返回数据            |
| data.list            | array          | 成功获取余额的玩家列表     |
| data.list\[].userid  | string         | 运营商的玩家ID        |
| data.list\[].balance | float          | 玩家当前可用余额        |
| data.erruseridlits   | array\[string] | 未找到或获取失败的玩家标识列表 |
| data.count           | integer        | 成功获取余额的玩家数量     |
| data.errcount        | integer        | 获取余额失败的玩家数量     |

* 玩家A余额 43.45，玩家B不存在。
*   示例：

    ```json
    {
        "code": 0,
        "error": "",
        "data": {
            "list": [
                {
                    "userid": "trZXIUZt-1757388232303-DemoUser",
                    "balance": 43.45
                }
            ],
            "erruseridlits": [
                "jNfyOjhF-1757301369938-DemoUser"
            ],
            "count": 1,
            "errcount": 1
        }
    }
    ```
