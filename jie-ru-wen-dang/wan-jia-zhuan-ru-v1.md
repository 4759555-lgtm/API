# 玩家转入V1

## 1) 请求地址

> URL: {APIURL}/api/v1/player/transferIn

## 2) 请求参数:

| 参数名     | 类型            | 描述         |
| ------- | ------------- | ---------- |
| UserID  | string\[4-40] | 运营商的玩家唯一标识 |
| Amount  | float         | 转入金额 >0    |
| TraceId | string\[4-40] | 交易单号       |

* 示例：

```json
{
  "UserID": "user_id",
  "Amount": 123.45,
  "TraceId": "abc-def-gh"
}
```

## 3) 返回结果:

| 参数名          | 类型    | 描述      |
| ------------ | ----- | ------- |
| AfterBalance | float | 充值成功后余额 |

* 正常返回
* 示例：

```json
{
  "error": "",
  "data": {
    "AfterBalance": 123.45
   }
}
```

* 订单重复
* 示例：

```json
{
  "error": "Order already exists",
  "data": null
}
```
