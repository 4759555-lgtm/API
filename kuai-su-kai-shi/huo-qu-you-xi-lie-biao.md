---
icon: gamepad-modern
---

# 获取游戏列表

#### 获取游戏列表 <a href="#h3-u83b7u53d6u6e38u620fu5217u8868" id="h3-u83b7u53d6u6e38u620fu5217u8868"></a>

**1) 请求地址**

> URL: {APIURL}/api/v1/game/list

**2) 请求参数**

| 参数名      | 类型     | 描述            |
| -------- | ------ | ------------- |
| language | string | 语言设定 th, en … |

*   示例：

    ```json
    {
        "language": "string"
    }
    ```

请求示例代码：

```
curl --location --request POST 'https://hpgamecenter.pg-nmx.com/api/v1/game/list' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "language": "string"
}'
```

**3) 返回结果**

<table><thead><tr><th width="184">参数名</th><th width="176">类型</th><th>描述</th></tr></thead><tbody><tr><td>id</td><td>string</td><td>游戏ID</td></tr><tr><td>name</td><td>string</td><td>游戏名字</td></tr><tr><td>type</td><td>int</td><td>0: 拉霸游戏、电子游戏, 1: Mini游戏, 2: 视讯游戏,3: 捕鱼游戏, 4: 彩票游戏 （2,3,4后续更新开启）</td></tr><tr><td>icon_url</td><td>string</td><td>游戏icon</td></tr><tr><td>manufacturer</td><td>string</td><td>游戏厂商</td></tr><tr><td>portrait_icon_url</td><td>string</td><td>游戏icon(竖版)</td></tr></tbody></table>

*   示例：

    ```
    {
        "code": 200,
        "error": "",
        "data": {
            "list": [
                {
                    "id": "bg_1069564",
                    "name": "Gold Rush With Johnny",
                    "type": 0,
                    "icon_url": "/BHdownload/BG-1069564.webp",
                    "manufacturer": "bg",
                    "portrait_icon_url": "/BHdownload/bg_1069564_vertical.webp"
                },
                {
                    "id": "bg_1130491",
                    "name": "Lucky Lady Moon Megaways",
                    "type": 0,
                    "icon_url": "/BHdownload/BG-1130491.webp",
                    "manufacturer": "bg",
                    "portrait_icon_url": "/BHdownload/bg_1130491_vertical.webp"
                },
                {
                    "id": "bg_1248869",
                    "name": "Miss Cherry Fruits Jackpotparty",
                    "type": 0,
                    "icon_url": "/BHdownload/BG-1248869.webp",
                    "manufacturer": "bg",
                    "portrait_icon_url": "/BHdownload/bg_1248869_vertical.webp"
                },
                {
                    "id": "bg_1399448",
                    "name": "Wild Cash X 9990",
                    "type": 0,
                    "icon_url": "/BHdownload/BG-1399448.webp",
                    "manufacturer": "bg",
                    "portrait_icon_url": "/BHdownload/bg_1399448_vertical.webp"
                },
                {
                    "id": "bg_1511624",
                    "name": "Forty Fruity Million",
                    "type": 0,
                    "icon_url": "/BHdownload/BG-1511624.webp",
                    "manufacturer": "bg",
                    "portrait_icon_url": "/BHdownload/bg_1511624_vertical.webp"
                },
                {
                    "id": "bg_1576654",
                    "name": "Beer Bonanza",
                    "type": 0,
                    "icon_url": "/BHdownload/BG-1576654.webp",
                    "manufacturer": "bg",
                    "portrait_icon_url": "/BHdownload/bg_1576654_vertical.webp"
                },
                {
                    "id": "bg_1722553",
                    "name": "Halloween Bonanza",
                    "type": 0,
                    "icon_url": "/BHdownload/BG-1722553.webp",
                    "manufacturer": "bg",
                    "portrait_icon_url": "/BHdownload/bg_1722553_vertical.webp"
                },
                {
                    "id": "bg_1919510",
                    "name": "Gangsterz",
                    "type": 0,
                    "icon_url": "/BHdownload/BG-1919510.webp",
                    "manufacturer": "bg",
                    "portrait_icon_url": "/BHdownload/bg_1919510_vertical.webp"
                },
                {
                    "id": "bg_2049319",
                    "name": "Gift Rush",
                    "type": 0,
                    "icon_url": "/BHdownload/BG-2049319.webp",
                    "manufacturer": "bg",
                    "portrait_icon_url": "/BHdownload/bg_2049319_vertical.webp"
                },
                {
                    "id": "bg_2124595",
                    "name": "Soccermania",
                    "type": 0,
                    "icon_url": "/BHdownload/BG-2124595.webp",
                    "manufacturer": "bg",
                    "portrait_icon_url": "/BHdownload/bg_2124595_vertical.webp"
                },
                {
                    "id": "bg_2167551",
                    "name": "Potion Spells",
                    "type": 0,
                    "icon_url": "/BHdownload/BG-2167551.webp",
                    "manufacturer": "bg",
                    "portrait_icon_url": "/BHdownload/bg_2167551_vertical.webp"
                },
                {
                    "id": "bg_2167570",
                    "name": "Wild West Bonanza",
                    "type": 0,
                    "icon_url": "/BHdownload/BG-2167570.webp",
                    "manufacturer": "bg",
                    "portrait_icon_url": "/BHdownload/bg_2167570_vertical.webp"
                }
            ]
        }
    }
    ```
