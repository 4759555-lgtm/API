---
icon: coin-vertical
---

# 修改玩家余额

#### 修改玩家余额 <a href="#h3-u4feeu6539u73a9u5bb6u4f59u989d" id="h3-u4feeu6539u73a9u5bb6u4f59u989d"></a>

**1) 请求地址**

> URL: {OPURL}/Cash/TransferInOut

**2) 请求参数**

<table><thead><tr><th>参数名</th><th width="249">类型</th><th>描述</th></tr></thead><tbody><tr><td>appid</td><td>string</td><td>运营商唯一标识</td></tr><tr><td>userid</td><td>string</td><td>运营商的玩家唯一标识</td></tr><tr><td>tid</td><td>string</td><td>交易订单号</td></tr><tr><td>amount</td><td>float</td><td>增加/扣除金额 (+ 增加, - 扣除)</td></tr><tr><td>roundid</td><td>string</td><td>本局游戏ID</td></tr><tr><td>gameid</td><td>string</td><td>游戏ID</td></tr><tr><td>req_time</td><td>datetime</td><td>请求时间</td></tr><tr><td>reason</td><td>string</td><td>bet 下注扣款; win 派奖; refund 退回下注（红飞机）</td></tr><tr><td>is_end</td><td>bool</td><td>返奖时游戏结束标识 （true:当前对局已结束，false:当前对局未结束)</td></tr><tr><td>is_buy</td><td>bool</td><td>是否为购买freegame</td></tr><tr><td>bet</td><td>float</td><td>bet金额</td></tr></tbody></table>

* 如果我方在请求此接口时发生 Timeout 错误，可能会在接下来的一段时间内连续请求若干次。请使用 tid判断重复，确保幂等性。
* 运营商在处理本接口逻辑时需判断玩家余额是否大于下注值。如果玩家余额不足 ，则应返回一个报错信息给我方，错误编码非0即可,错误内容不能为空。否则会导致余额在游戏中为负数。
*   示例：

    ```json
    {
    "tid":"d3mauo8db2sontriomug",
    "userid":"aaa",
    "appid":"z15_AMD_1",
    "amount":0,
    "roundid":"d3mauo8db2sph3kmeke0",
    "gameid":"pg_100",
    "req_time":1760341857,
    "reason":"win",
    "is_end":true,
    "is_buy":false,
    "bet":0
    }
    ```

**3) 返回结果**

| 参数名     | 类型    | 描述          |
| ------- | ----- | ----------- |
| balance | float | 修改后玩家当前可用余额 |

*   示例：\
    玩家余额减少10时：

    ```json
    {
    "code": 0,
    "error": "",
    "data": {
      "balance": 11004,
     }
    }
    ```
*   报错示例：\
    注意：不能多传额外的字段。

    ```json
    {
    "code": 1000,
    "error": "some error occur!!"
    }
    ```
