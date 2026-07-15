---
icon: calculator
---

# 调整个人fish游戏RTP



#### 调整个人RTP <a href="#h3--rtp" id="h3--rtp"></a>

**1) 请求地址**

> URL: {APIURL}/api/v1/player/fish/setRtp

**2) 请求参数**

| 参数名    | 类型     | 是否必填 | 说明                                          |
| ------ | ------ | ---- | ------------------------------------------- |
| userid | string | 是    | 玩家唯一标识；单玩家：传入单个 userid；多玩家：多个 userid 英文逗号分隔 |
| rtp    | int    | 是    | 玩家基础返还比例，取值范围 0\~100，代表百分比                  |
| gameid | string | 是    | 捕鱼游戏 ID；单游戏：单个 gameid；多游戏：多个 gameid 英文逗号分隔  |

*   示例(单个玩家)：

    ```json
    {
        "userid": "pnXnijvv-1781487540411-DemoUser",
        "rtp": 20,
        "gameid": "jilifish_289_fish15"
    }
    ```
*   示例(多个玩家)：

    ```json
    {
       "userid": "WYdKadVj-1732180150061-DemoUser,aPHXsPXM-1732241836229-DemoUser,dPXQlbNp-1732241919276-DemoUser",
       "rtp": 30,
       "gameid": "jilifish_289_fish15"
    }
    ```

**请求示例代码：**

```bash
curl --location --request POST 'https://{APIURL}/api/v1/player/fish/setRtp' \
--header 'X-Sign: 接口签名值' \
--header 'X-Request-Id: 自定义唯一请求ID' \
--header 'X-Appid: 业务渠道ID' \
--header 'Content-Type: application/json' \
--data-raw '{
    "userid":"pnXnijvv-1781487540411-DemoUser",
    "rtp":20,
    "gameid":"jilifish_289_fish15,jdbfish_7003,pg_100"
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
              102563
          ]
      }
    }
    ```
