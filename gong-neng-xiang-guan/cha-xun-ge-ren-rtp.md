---
icon: book-quran
---

# 查询个人RTP

## 查询个人RTP

### 1) 请求地址

> URL: `{APIURL}/api/v2/player/getRtpList`

***

### 2) 请求参数

| 参数名      | 类型     | 必填  | 描述                                                                                                                |
| -------- | ------ | --- | ----------------------------------------------------------------------------------------------------------------- |
| userid   | string | 是   | 运营商的玩家唯一标识                                                                                                        |
| gameid   | string | 是   | <p>被控制RTP的游戏ID<br><strong>注意</strong>: 填写<code>ALL</code>时查询全部游戏</p>                                              |
| page     | int64  | 是   | 页码，从1开始                                                                                                           |
| pagesize | int64  | 是   | 每页大小，最大500                                                                                                        |
| status   | int    | 是   | <p>点控状态<br><strong>-1</strong>: 查询全部状态的点控记录<br><strong>0</strong>: 已失效状态的点控记录<br><strong>1</strong>: 生效中的点控记录</p> |

#### 请求示例

```json
{
  "uid": "f-09261620",
  "gameid": "pg_100",
  "page": 1,
  "pagesize": 50,
  "status": 1,
}
```

#### 请求示例代码

```bash
curl --location --request POST '{APIURL}/api/v2/player/getRtpList' \
--header 'Content-Type: application/json' \
--data-raw '{
  "userid": "f-09261620",
  "gameid": "pg_100",
  "page": 1,
  "pagesize": 50,
  "status": 1,

}'
```

***

### 3) 返回结果

#### 响应参数说明

| 参数名                     | 类型      | 层级  | 描述               |
| ----------------------- | ------- | --- | ---------------- |
| code                    | integer | 1   | 状态码，0表示成功        |
| error                   | string  | 1   | 错误信息，成功时为空       |
| data                    | object  | 1   | 返回数据             |
| list                    | array   | 2   | RTP配置列表          |
| gameid                  | string  | 3   | 游戏ID             |
| control\_time           | string  | 3   | 创建时间（ISO 8601格式） |
| userid                  | string  | 3   | 运营商的玩家唯一标识       |
| pid                     | integer | 3   | 玩家唯一标识           |
| game\_name              | string  | 3   | 游戏名称             |
| game\_rtp               | integer | 3   | 商户配置游戏RTP配置值     |
| control\_rtp            | integer | 3   | 点控RTP配置值         |
| controlling\_rtp        | integer | 3   | 当前玩家实际RTP值       |
| person\_win\_max\_mult  | integer | 3   | 玩家最大赢分倍数         |
| person\_win\_max\_score | integer | 3   | 玩家最大赢分           |
| restrictions\_max\_rtp  | integer | 3   | 玩家终身最大RTP限制      |
| experience              | integer | 3   | RTP类型/体验类型       |
| rtp\_config\_off        | integer | 2   | RTP点控开关状态        |
| count                   | integer | 2   | 总记录数             |

#### 返回示例

```json
{
  "code": 0,
  "error": "",
  "data": {
    "list": [
      {
        "gameid": "pg_100",
        "control_time": "2025-10-14T06:37:34.25Z",
        "userid": "f-09261620",
        "pid": 172244,
        "game_name": "【100】Candy Bonanza",
        "game_rtp": 93,
        "control_rtp": 70,
        "controlling_rtp": 0,
        "person_win_max_mult": 30,
        "person_win_max_score": 1,
        "restrictions_max_rtp": 0,
        "experience": 0
      }
    ],
    "rtp_config_off": 0,
    "count": 1
  }
}
```

***
