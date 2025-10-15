---
icon: joystick
---

# 获取游戏登录 URL

#### 获取游戏登录 URL <a href="#h3--url" id="h3--url"></a>

**1) 请求地址**

> URL: {APIURL}/api/v1/game/launch

**2) 请求参数:**

| 参数名      | 类型            | 描述            |
| -------- | ------------- | ------------- |
| userid   | string\[4-40] | 运营商玩家唯一标识     |
| gameid   | string        | 游戏 ID         |
| Language | string        | 语言设定 th, en … |

* 示例：
  
  ```json
  {
      "userid": "abc",
      "gameid": "pg_98",
      "language": "th"
  }
  ```

请求示例代码：

```bash
curl --location --request POST 'https://{APIURL}/api/v1/game/launch' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "userid": "abc",
    "gameid": "pg_98",
    "language": "th"
}'
```

**3) 返回结果:**

| 参数名 | 类型     | 描述      |
| --- | ------ | ------- |
| url | string | 游戏登录URL |

* 示例：
  
  <pre class="language-json"><code class="lang-json"><strong>{
  </strong>"code": 0,
  "error": "",
  "data": {
    "url": "https://popapi.cc/pg_98/index.html?l=th&#x26;t=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxODcsIlMiOjEwMDIsIkQiOiJYaW5nWXVuWGlhbmcifQ.9td-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxmw"
   }
  }
  </code></pre>
