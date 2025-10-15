---
icon: book-quran
---

# 查询个人RTP

## 查询个人RTP

### 1) 请求地址

URL: `{APIURL}/api/v2/player/getRtpList`

***

### 2) 请求参数

| 参数名      | 类型     | 必填 | 描述                                                                                                                         |
| -------- | ------ | -- | -------------------------------------------------------------------------------------------------------------------------- |
| uid      | string | 是  | 运营商的玩家唯一标识                                                                                                                 |
| gameid   | string | 是  | <p>被控制RTP的游戏ID<br><strong>注意</strong>: 填写<code>ALL</code>时查询全部游戏</p>                                                       |
| page     | int64  | 是  | 页码，从1开始                                                                                                                    |
| pagesize | int64  | 是  | 每页大小，最大500                                                                                                                 |
| status   | int    | 是  | <p>点控状态<br><strong>-1</strong>: 全部<br><strong>0</strong>: 完成点控<br><strong>1</strong>: 点控中</p>                              |
| lang     | string | 否  | <p>使用者语言<br>可选值: <code>es</code>, <code>idr</code>, <code>it</code>, <code>th</code>, <code>zh</code>, <code>en</code></p> |

#### 请求示例

```json
{
  "uid": "f-09261620",
  "gameid": "pg_100",
  "page": 1,
  "pagesize": 50,
  "status": 1,
  "lang": "en"
}
```

#### 请求示例代码

```bash
curl --location --request POST '{APIURL}/api/v2/player/getRtpList' \
--header 'Content-Type: application/json' \
--data-raw '{
  "uid": "f-09261620",
  "gameid": "pg_100",
  "page": 1,
  "pagesize": 50,
  "status": 1,
  "lang": "en"
}'
```

***

### 3) 返回结果

#### 响应参数说明

| 参数名                     | 类型      | 层级 | 描述               |
| ----------------------- | ------- | -- | ---------------- |
| code                    | integer | 1  | 状态码，0表示成功        |
| error                   | string  | 1  | 错误信息，成功时为空       |
| data                    | object  | 1  | 返回数据             |
| list                    | array   | 2  | RTP配置列表          |
| operatorid              | string  | 3  | 运营商ID            |
| gameid                  | string  | 3  | 游戏ID             |
| control\_time           | string  | 3  | 创建时间（ISO 8601格式） |
| uid                     | string  | 3  | 运营商的玩家唯一标识       |
| pid                     | integer | 3  | 玩家唯一标识           |
| game\_name              | string  | 3  | 游戏名称             |
| game\_rtp               | integer | 3  | 游戏配置RTP          |
| play\_history\_rtp      | integer | 3  | 玩家历史RTP          |
| control\_rtp            | integer | 3  | 账号RTP            |
| controlling\_rtp        | integer | 3  | 当前RTP            |
| auto\_remove\_rtp       | integer | 3  | 自动解除RTP          |
| person\_win\_max\_mult  | integer | 3  | 玩家最大赢分倍数         |
| person\_win\_max\_score | integer | 3  | 玩家最大赢分           |
| restrictions\_max\_rtp  | integer | 3  | 玩家终身最大RTP限制      |
| experience              | integer | 3  | RTP类型/体验类型       |
| rtp\_config\_off        | integer | 2  | RTP配置开关状态        |
| count                   | integer | 2  | 总记录数             |

#### 返回示例

```json
{
  "code": 0,
  "error": "",
  "data": {
    "list": [
      {
        "operatorid": "qwe456_USD_1",
        "gameid": "pg_100",
        "control_time": "2025-10-14T06:37:34.25Z",
        "uid": "f-09261620",
        "pid": 172244,
        "game_name": "【100】Candy Bonanza",
        "game_rtp": 93,
        "play_history_rtp": 0,
        "control_rtp": 70,
        "controlling_rtp": 0,
        "auto_remove_rtp": 80,
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
