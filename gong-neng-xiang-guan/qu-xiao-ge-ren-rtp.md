---
icon: empty-set
---

# 取消个人RTP

#### 取消个人RTP

**1) 请求地址**

> URL: {APIURL}/api/v2/player/cancelRtp

**2) 请求参数**

| 参数名       | 类型     | 描述                                       |
| --------- | ------ | ---------------------------------------- |
| uids      | string | 需要取消的玩家id列表                              |
| gameid    | string | 取消控制RTP的游戏id，游戏id为`ALL`时取消的是设置rtp时的`ALL` |
| starttime | string | 起始时间(UTC时间戳)                             |
| endtime   | string | 结束时间(UTC时间戳)                             |

* 示例(单个玩家)：

```json
{
    "userids": [
        "f-09261620"
    ],
    "startTime": 1760581729494,
    "endTime": 1760581729494,
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
  "startTime": 1760581729494,
    "endTime": 1760581729494,
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
