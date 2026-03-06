---
icon: list-ol
---

# 查询订单

#### 查询订单 <a href="#h3-u67e5u8be2u8ba2u5355" id="h3-u67e5u8be2u8ba2u5355"></a>

**1) 请求地址**

> URL: {APIURL}/api/v1/transaction/queryOrder

* 注: 转入转出后, 如果api调用超时, 通常需要调用此接口检查订单状态

**2) 请求参数:**

| 参数名     | 类型            | 必填 | 描述   |
| ------- | ------------- | -- | ---- |
| traceid | string\[4-40] | 是  | 交易单号 |

*   示例：

    ```json
    {
    "traceid": "fdsafaagg1234"
    }
    ```

**请求示例代码**

```bash
curl --location --request POST 'https://{APIURL}/api/v1/transaction/queryOrder' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "traceid": "fdsafaagg1234"
}'
```

**3) 返回结果:**

<table><thead><tr><th width="249">参数名</th><th>类型</th><th>描述</th></tr></thead><tbody><tr><td>data.id</td><td>string</td><td>平台交易订单号</td></tr><tr><td>data.traceid</td><td>string</td><td>交易单号</td></tr><tr><td>data.create_time</td><td>datetime</td><td>订单创建时间，毫秒级时间戳</td></tr><tr><td>data.pid</td><td>int64</td><td>平台唯一ID</td></tr><tr><td>data.userid</td><td>string</td><td>运营商的玩家ID</td></tr><tr><td>data.appid</td><td>string</td><td>商户appid</td></tr><tr><td>data.amount</td><td>float</td><td>转入/转出总额</td></tr><tr><td>data.action</td><td>string</td><td>in,out,allout 转入,转出,全部转出</td></tr><tr><td>data.error</td><td>string</td><td>订单执行的错误信息, 如果是”” 表示成功</td></tr><tr><td>data.completed</td><td>bool</td><td>订单是否执行完成, 如果是false, 请稍等再重新使用此接口检查</td></tr></tbody></table>

* 正常成功的订单
*   示例：

    ```json
    {
        "code": 0,
        "error": "",
        "data": {
            "order": {
                "id": "d3djos0db2suqrs2ko90",
                "appid": "qwe456_USD_1",
                "traceid": "abc-def-gh",
                "create_time": 1759198319907,
                "pid": 173966,
                "userid": "aaa",
                "amount": 123.45,
                "action": "in",
                "error": "",
                "completed": true
            }
        }
    }
    ```
* 订单存在但是转账失败
*   示例：

    ```json
    {
        "code": 1,
        "error": "Order already exists1",
        "data": null
    }
    ```
* 订单不存在
*   示例：

    ```json
    {
        "code": 1,
        "error": "sql: no rows in result set",
        "data": null
    }
    ```
