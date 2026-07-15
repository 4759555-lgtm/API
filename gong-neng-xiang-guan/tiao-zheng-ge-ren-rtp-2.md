---
icon: calculator
---

# 调整个人mini游戏RTP



#### 调整个人RTP <a href="#h3--rtp" id="h3--rtp"></a>

**1) 请求地址**

> URL: {APIURL}/api/v1/player/mini/setRtp

**2) 请求参数**

| 参数名                     | 类型     | 是否必填 | 说明                                       |
| ----------------------- | ------ | ---- | ---------------------------------------- |
| userid                  | string | 是    | 玩家唯一标识；单玩家传单个 ID，多玩家用**英文逗号**拼接多个 userid |
| rtp                     | int    | 是    | 玩家基础返还比例，取值区间 0\~100                     |
| gameid                  | string | 是    | 小游戏游戏 ID，多游戏可英文逗号分隔                      |
| person\_win\_max\_mult  | int    | 是    | 单人单局最大赢取倍率                               |
| person\_win\_max\_score | int    | 是    | 单人单次可赢取最大积分                              |

*   示例(单个玩家)：

    ```json
    {
        "userid": "pnXnijvv-1781487540411-DemoUser",
        "rtp": 80,
        "gameid": "spribe_goal",
        "person_win_max_mult": 30,
        "person_win_max_score": 100000
    }
    ```
*   示例(多个玩家)：

    ```json
    {
        "userid": "pnXnijvv-1781487540411-DemoUser,test_user01-12345-DemoUser",
        "rtp": 80,
        "gameid": "spribe_goal,spribe_dice",
        "person_win_max_mult": 30,
        "person_win_max_score": 100000
    }
    ```

**请求示例代码：**

```bash
curl --location --request POST 'https://{APIURL}/api/v1/player/mini/setRtp' \
--header 'X-Sign: 签名内容' \
--header 'X-Request-Id: 随机唯一请求ID' \
--header 'X-Appid: 渠道AppId' \
--header 'Content-Type: application/json' \
--data-raw '{
    "userid":"pnXnijvv-1781487540411-DemoUser",
    "rtp":80,
    "gameid":"spribe_goal",
    "person_win_max_mult":30,
    "person_win_max_score":100000
}'
```

**3) 返回结果**

| 参数名       | 类型       | 描述     |
| --------- | -------- | ------ |
| pid\_list | \[]int64 | 平台唯一ID |

*   示例：

    ```json
    {
      "code": 0,
      "error": "",
      "data": {
          "pid_list": [
              102561,
              102562,
              102563
          ]
      }
    }
    ```
