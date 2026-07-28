---
icon: xmark-large
---

# 停用/恢复玩家（测试中）

## 停用/恢复玩家

**停用/恢复玩家**

**1) 请求地址**

> URL: `{APIURL}/api/v2/player/ban`

**2) 请求参数**

| 参数名    | 类型     | 必填 | 描述                     |
| ------ | ------ | -- | ---------------------- |
| userid | string | 是  | 需要停用或恢复的运营商玩家ID        |
| status | int    | 是  | 玩家状态：`0` 表示停用，`1` 表示正常 |

* 示例（停用玩家）：

```
{
  "userid": "f-09261620",
  "status": 0
}
```

* 示例（恢复玩家）：

```
{
  "userid": "f-09261620",
  "status": 1
}
```

**请求示例代码：**

```
curl --location --request POST 'https://{APIURL}/api/v2/player/ban' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
  "userid": "f-09261620",
  "status": 0
}'
```

**3) 返回结果**

| 参数名   | 类型     | 描述                      |
| ----- | ------ | ----------------------- |
| code  | int    | 返回码，`0` 表示成功，非 `0` 表示失败 |
| error | string | 错误信息，成功时为空字符串           |
| data  | object | 返回数据，无数据时为 `null`       |

* 成功示例：

```
{
  "code": 0,
  "error": "",
  "data": null
}
```

* 玩家账号不存在：

```
{
  "code": 2001,
  "error": "Player account does not exist",
  "data": null
}
```

**错误码说明：**

| 错误码  | 错误信息                          | 描述      |
| ---- | ----------------------------- | ------- |
| 2001 | Player account does not exist | 玩家账号不存在 |
