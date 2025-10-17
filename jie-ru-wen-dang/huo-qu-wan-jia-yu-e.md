# 获取玩家余额

## 1) 请求地址

> URL: {APIURL}/api/v1/player/balance

## 2) 请求参数:

| 参数名    | 类型            | 描述         |
| ------ | ------------- | ---------- |
| UserID | string\[4-40] | 运营商的玩家唯一标识 |

* 示例：

```json
{
  "UserID": "testuser1",
  "AppID": "fake",
  "AppSecret": "1234-abcd-xxxkkk"
}
```

## 3) 返回结果:

| 参数名              | 类型    | 描述                          |
| ---------------- | ----- | --------------------------- |
| Balance          | float | 玩家当前可用余额                    |
| Unsettled        | float | 投注后尚未结算的余额 **deprecated**   |
| UnsettledDetails | map   | 投注后尚未结算的余额详情 **deprecated** |

* 玩家共有 143.45，其中投注 pg\_98 有 20 尚未结算，投注 pg\_65 有 80 尚未结算。
* Unsettled 和 UnsettledDetails 已废弃，请使用 APIURL/api/v1/player/pendinggames 接口实现相关逻辑。
* 示例：

```json
{
  "code": 0,
  "error": "",
  "data": {
    "Balance": 43.45,
    "Unsettled": 100,
    "UnsettledDetails": {
      "pg_98": 20,
      "pg_65": 80
    }
   }
}
```
