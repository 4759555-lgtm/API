---
icon: calculator-simple
---

# 商户RTP调控

#### 商户RTP调控 <a href="#h3--rtp-v2" id="h3--rtp-v2"></a>

**1) 请求地址**

> URL: {APIURL}/api/v2/operator/setRtp

**2) 请求参数**

| 参数名              | 类型     | 描述                                                                                                                                                                                                                       |
| ---------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| game\_pattern    | int    | 游戏类型，可填值`1：心跳型，2：波动型，3：仿正型，4：混合型，5：稳定型，6：高中奖率，7：超高中奖率`                                                                                                                                                                   |
| rtp              | int    | 设置玩家控制的RTP值，可填值`10, 20, 30, 40, 50, 60, 70, 80, 85, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99, 100, 102, 105, 110, 120, 130, 140, 150, 160, 170, 180, 190, 200, 220, 240, 260, 280, 300`注意，根据运营商权限不同，可能仅支持10-97或93-300的RTP值 |
| gameid           | string | 被控制RTP的游戏id，游戏id为`ALL`时为全部slots游戏(不包括其他类型游戏)，调控多个游戏用`","`(英文逗号)分割                                                                                                                                                        |
| game\_type       | int    | 0: 拉霸游戏, 1: Mini游戏, 2: 视讯游戏,3: 捕鱼游戏, 4: 彩票游戏 （2,3,4后续更新开启）                                                                                                                                                               |
| max\_multiple    | int    | 最大赢钱倍数，非必填项，如果不填设置默认值100。当设置的值为非0值时，`最小值`为`1`，`最大值`为`10000`，当填写的值不在范围内将会报错。                                                                                                                                              |
| max\_win\_points | int    | 最大赢钱数，非必填项，如果不填设置默认值1000000。当设置的值为非0值时，`最小值`为`1`，`最大值`为`100000000`，当填写的值不在范围内将会报错。                                                                                                                                       |

*   示例：

    ```json
    {
    "game_pattern": 1,
    "rtp": 30,
    "game_id": "pg_1381200",
    "AppID": "qwe456_USD_1",
    "Sign": "34d5f21a93efff68f55f891d211ad5bb"
    }
    ```

请求示例代码：

```powershell
curl --location --request POST 'https://hpgamecenter.pg-nmx.com/api/v2/operator/setRtp' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "game_pattern": 0,
    "rtp": 0,
    "gameid": "string",
    "game_type": 0,
    "buy_rtp": 0,
    "max_win_points": 0,
    "max_multiple": 0
}'
```

**3) 返回结果**

| 参数名     | 类型    | 描述   |
| ------- | ----- | ---- |
| app\_id | sting | 商户id |

*   示例：

    ```json
    {
      "code": 0,
      "error": "",
      "data": {
          "app_id": "qwe456"
      }
    }
    ```
