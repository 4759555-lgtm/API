---
icon: empty-set
---

# 取消个人RTP

#### 取消个人RTP

**1) 请求地址**

> URL: {APIURL}/api/v2/player/cancelRtp

**2) 请求参数**

| 参数名     | 类型     | 描述                                                                                                                             |
| ------- | ------ | ------------------------------------------------------------------------------------------------------------------------------ |
| userids | string | 需要取消的玩家id列表                                                                                                                    |
| gameid  | string | <p>取消控制RTP的游戏id，当游戏 ID 设置为 <code>ALL</code> 时，表示取消对所有游戏的 RTP 控制。<br>注意：若配置针对特定游戏 ID，使用 <code>ALL</code> 不会取消该特定游戏的 RTP 控制。</p> |

* 示例(单个玩家)：

```json
{
    "userids": [
        "f-09261620"
    ],
    "gameid": [
        "ALL"
    ]
}
```

**请求示例代码：**

```bash
curl --location --request POST 'https://{APIURL}/api/v2/player/cancelRtp' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
  "userids": [
    "f-09261620"
  ],
    "gameid": [
        "ALL"
  ]
}'
```

**3) 返回结果**

| 参数名       | 类型    | 描述        |
| --------- | ----- | --------- |
| pid\_list | int64 | 用户的唯一标识列表 |

* 示例：

```json
{
    "code": 0,
    "error": "",
    "data": {
        "pid_list": [100010]
    }
}
```
