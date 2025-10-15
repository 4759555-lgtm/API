---
icon: list-ol
---

# 查询订单

#### 查询订单 <a href="#h3-u67e5u8be2u8ba2u5355" id="h3-u67e5u8be2u8ba2u5355"></a>

**1) 请求地址**

> URL: {APIURL}/api/v1/transaction/queryOrder

* 注: 转入转出后, 如果api调用超时, 通常需要调用此接口检查订单状态

**2) 请求参数:**

| 参数名     | 类型            | 描述   |
| ------- | ------------- | ---- |
| traceid | string\[4-40] | 交易单号 |

*   示例：

    ```json
    {
    "traceid": "fdsafaagg1234"
    }
    ```

**请求示例代码**

```powershell
curl --location --request POST 'https://hpgamecenter.pg-nmx.com/api/v1/transaction/queryOrder' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "traceid": "string"
}'
```

**3) 返回结果:**

| 参数名          | 类型       | 描述                                |
| ------------ | -------- | --------------------------------- |
| id           | string   | 平台内部唯一ID                          |
| trace\_id    | string   | 交易单号                              |
| create\_time | datetime | 订单创建时间                            |
| pid          | int64    | 平台内部玩家id                          |
| user\_id     | string   | operator玩家id                      |
| app\_id      | string   | 运营商标识                             |
| amount       | float    | 转入/转出总额                           |
| action       | string   | in,out,allout 转入,转出,全部转出          |
| error        | string   | 订单执行的错误信息, 如果是”” 表示成功             |
| completed    | bool     | 订单是否执行完成, 如果是false, 请稍等再重新使用此接口检查 |

* 正常成功的订单
*   示例：

    ```json
    {
        "code": 0,
        "error": "",
        "data": {
            "order": {
                "id": "d3djos0db2suqrs2ko90",
                "app_id": "qwe456_USD_1",
                "trace_id": "abc-def-gh",
                "create_time": 1759198319907,
                "pid": 173966,
                "user_id": "aaa",
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
    "code": 1000,
    "error": "error",
    "data": {
      "order": {
        "id": "d3djos0db2suqrs2ko90",
        "trace_id": "fdsafaagg1234",
        "create_time": "2023-12-07T10:55:42.15+08:00",
        "pid": 100065,
        "user_id": "user_id",
        "app_id": "faketrans",
        "amount": 123.45,
        "action": "outall",
        "error": "some internal error occur",
        "completed": true
      }
     }
    }
    ```
* 订单不存在
*   示例：

    ```json
    {
    "code": 1000,
    "error": "Order does not exist"
    }
    ```
