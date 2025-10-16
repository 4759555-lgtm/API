---
icon: file-waveform
---

# 下注历史

#### 拉取下注历史 <a href="#h3-u62c9u53d6u4e0bu6ce8u5386u53f2" id="h3-u62c9u53d6u4e0bu6ce8u5386u53f2"></a>

注意：仅支持查询60天内的数据。基于性能考量一次性查询条数<mark style="color:red;">最大为10000</mark>，且每分钟<mark style="color:red;">最多拉取60次</mark>。

**1) 请求地址**

> URL: {APIURL}/api/v1/record/getbetlogs

**2) 请求参数**

| 参数        | 类型     | 说明                                                                |
| --------- | ------ | ----------------------------------------------------------------- |
| userid    | string | 运营商的玩家唯一标识（可不填，不填查询所有玩家）                                          |
| gameid    | string | 游戏ID（可不填，不填查询所有游戏）                                                |
| starttime | Int    | 查询起始时间(UTC时间戳)                                                    |
| endtime   | Int    | 查询结束时间(UTC时间戳)                                                    |
| page      | Int    | 当前页                                                               |
| pagesize  | Int    | 查询条数。注意：单次查询最多不能超过10000条                                          |
| sort      | Bool   | <p>排序方式，非必填项，不填为默认值false，返回结果按时间降序排序。<br>当值为true时，返回结果按时间升序排序</p> |

*   示例：

    ```json
    {
      "userid": "111",
      "gameid": "pg_98",
      "starttime": 1730390400,
      "endtime": 1734969599,
      "pagesize": 20,
      "page": 1,
      "sort":true
    }
    ```

**请求示例代码**

```bash
curl --location --request POST 'https://{APIURL}/api/v1/record/getbetlogs' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "userid": "string",
    "gameid": "string",
    "starttime": 1730390400,
    "endtime": 1734969599,
    "pagesize": 20,
    "page": 1,
    "sort": true
}'
```

**3) 返回结果**

**返回结果默认按时间降序排序（新插入的数据优先展示在前面）**\
**当请求参数`Sort`值为true时返回结果按时间升序排序（老数据优先展示在前面）**

| 参数名          | 类型            | 描述               |
| ------------ | ------------- | ---------------- |
| id           | string        | 记录的唯一ID          |
| pid          | int64         | 平台玩家ID           |
| userid       | string\[4-40] | 运营商的玩家唯一标识       |
| gameid       | string        | 游戏ID             |
| bet          | float         | 下注总额             |
| win          | float         | 赢分总额             |
| winlose      | float         | 净输赢              |
| insert\_time | datetime      | 记录入库的时间          |
| appid        | string        | 运营商ID            |
| balance      | float         | 结算后余额            |
| grade        | int           | 投注档位             |
| completed    | boolean       | 本轮游戏是否完成         |
| roundid      | string        | 回合ID, 同一局游戏该字段相同 |

*   示例：

    ```json
    {
        "code": 0,
        "error": "",
        "data": {
            "list": [
                {
                    "id": "d3dim10db2sst828u8og",
                    "pid": 172349,
                    "userid": "FecXhmSl-1759021920907-DemoUser",
                    "gameid": "pp_vs9aztecgemsdx",
                    "bet": 0.45,
                    "win": 0,
                    "insert_time": 1759193860599,
                    "appid": "qwe456_USD_1",
                    "balance": 100295.99,
                    "winlose": -0.45,
                    "grade": 0,
                    "completed": true,
                    "roundid": "d3dim10db2sst828u8og"
                },
                {
                    "id": "d3dim78db2sst828u8pg",
                    "pid": 172349,
                    "userid": "FecXhmSl-1759021920907-DemoUser",
                    "gameid": "pp_vs9aztecgemsdx",
                    "bet": 9,
                    "win": 0,
                    "insert_time": 1759193885064,
                    "appid": "qwe456_USD_1",
                    "balance": 100307.99,
                    "winlose": -9,
                    "grade": 9,
                    "completed": true,
                    "roundid": "d3dim78db2sst828u8pg"
                },
                {
                    "id": "d3dimjgdb2sst828u90gEnd",
                    "pid": 172349,
                    "userid": "FecXhmSl-1759021920907-DemoUser",
                    "gameid": "pp_vs9aztecgemsdx",
                    "bet": 0,
                    "win": 28,
                    "insert_time": 1759193934544,
                    "appid": "qwe456_USD_1",
                    "balance": 100233.99,
                    "winlose": 28,
                    "grade": 9,
                    "completed": true,
                    "roundID": "d3dimjgdb2sst828u90g"
                }
            ],
            "all": 20
        }
    }
    ```
