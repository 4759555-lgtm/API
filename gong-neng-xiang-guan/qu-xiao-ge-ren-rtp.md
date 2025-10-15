---
icon: empty-set
---

# 取消个人RTP

#### 取消个人RTP

**1) 请求地址**

> URL: {APIURL}/api/v2/player/cancelRtp

**2) 请求参数**

| 参数名    | 类型         | 描述                                                                            |
| ------ | ---------- | ----------------------------------------------------------------------------- |
| uids   | \[]string  | 需要取消的玩家id列表                                                                   |
| gameid | \[]string  | 取消控制RTP的游戏id，游戏id为`ALL`时取消的是设置rtp时的`ALL`                                      |
| fromto | \[2]string | 输入一个长度为2的字符串数组来筛选该时间段创建的rtp数据 `["YYYY-MM-DD HH:mm:ss","YYYY-MM-DD HH:mm:ss"]` |

* 示例(单个玩家)：

```json
{
    "uids": [
        "f-09261620"
    ],
    "fromto": [
        "2025-10-09 00:00:00",
        "2025-10-10 00:00:00"
    ],
    "gameid": [
        "ALL"
    ]
}
```

**请求示例代码：**

```powershell
curl --location --request POST 'https://hpgamecenter.pg-nmx.com/api/v2/player/cancelRtp' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
  "pids": [],
  "uids": [
    "f-09261620"
  ],
  "fromto": [
    "2025-10-09 00:00:00",
    "2025-10-10 00:00:00"
  ],
  "gameid": [
    "ALL"
  ]
}'
```

**3) 返回结果**

| 参数名       | 类型       | 描述        |
| --------- | -------- | --------- |
| pid\_list | \[]int64 | 用户的唯一标识列表 |

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
