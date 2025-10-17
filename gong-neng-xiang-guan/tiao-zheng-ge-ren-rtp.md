---
icon: calculator
---

# 调整个人RTP

#### 调整个人RTP <a href="#h3--rtp" id="h3--rtp"></a>

**1) 请求地址**

> URL: {APIURL}/api/v1/player/setRtp

**2) 请求参数**

| 参数名                     | 类型     | 描述                                                                                                                                                                                                                                                               |
| ----------------------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| userid                  | string | 运营商的玩家唯一标识，设置多个玩家，玩家id之间使用`","`(英文逗号)分割。注意，批量设置数据量过大时，会有一分钟左右的生效延迟。                                                                                                                                                                                              |
| rtp                     | int    | 设置玩家控制的RTP值，可填值`10, 20, 30, 40, 50, 60, 70, 80, 85, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99, 100, 102, 105, 110, 120, 130, 140, 150, 160, 170, 180, 190, 200, 220, 240, 260, 280, 300`注意，根据运营商权限不同，可能仅支持10-97或93-300的RTP值                                         |
| gameid                  | string | 被控制RTP的游戏id，游戏id为`ALL`时为全部slots游戏(不包括其他类型游戏)，调控多个游戏用`","`(英文逗号)分割                                                                                                                                                                                                |
| game\_pattern           | int    | 游戏类型，可填值1：波动型，2：仿正型，3：混合型，4：稳定型，5：高中奖率                                                                                                                                                                                                                           |
| remove\_rtp             | int    | 非必填项，如果不填则不会解除RTP控制。解除RTP管控的值，当用户RTP达到此值将解除用户的RTP控制，可填值`10, 20, 30, 40, 50, 60, 70, 80, 85, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99, 100, 102, 105, 110, 120, 130, 140, 150, 160, 170, 180, 190, 200, 220, 240, 260, 280, 300`注意，根据运营商权限不同，可能仅支持10-97或93-300的RTP值 |
| person\_win\_max\_mult  | int    | 最大赢钱倍数(非必填项)，如果不填设置默认值100。当填写非0值时，数值需满足 1 ≤ 数值 ≤ 10000，超出此范围将提示错误。                                                                                                                                                                                               |
| person\_win\_max\_score | int    | 最大赢钱数(非必填项)，如果不填设置默认值1000000。当填写非0值时，数值需满足 1 ≤ 数值 ≤ 100000000，超出此范围将提示错误。                                                                                                                                                                                        |
| person\_win\_max\_rtp   | int    | 最大RTP（非必填项，单位：%）。若不填写，默认值为 0（表示不生效，即不设置上限）。当填写非0值时，数值需满足 1 ≤ 数值 ≤ 1000，超出此范围将提示错误。                                                                                                                                                                               |

*   示例(单个玩家)：

    ```json
    {
      "userid": "LpyQnuYP-1732619999024-DemoUser",
      "rtp": 70,
      "gameid": "pg_100",
      "game_pattern": 1,
      "remove_rtp": 80,
      "person_win_max_mult":30,
      "person_win_max_score":1,
      "person_win_max_rtp":100,
    }
    ```
*   示例(多个玩家)：

    ```json
    {
       "userid": "WYdKadVj-1732180150061-DemoUser,aPHXsPXM-1732241836229-DemoUser,dPXQlbNp-1732241919276-DemoUser",
       "rtp": 30,
       "gameid": "pg_100,pg_89",
       "game_pattern": 1,
       "remove_rtp": 70,
       "person_win_max_mult":30,
       "person_win_max_score":1,,
       "person_win_max_rtp":100,
    }
    ```

**请求示例代码：**

```bash
curl --location --request POST 'https://{APIURL}/api/v1/player/setRtp' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "userid": "string",
    "rtp": 30,
    "gameid": "string",
    "game_pattern": 1,
    "remove_rtp": 70,
    "person_win_max_mult": 30,
    "person_win_max_score": 1,
    "person_win_max_rtp":100,
}'
```

**3) 返回结果**

| 参数名       | 类型       | 描述        |
| --------- | -------- | --------- |
| pid\_list | \[]int64 | 用户的唯一标识列表 |

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
