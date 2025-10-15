---
icon: sack-dollar
---

# 获取玩家余额

#### 获取玩家余额 <a href="#h3-u83b7u53d6u73a9u5bb6u4f59u989d" id="h3-u83b7u53d6u73a9u5bb6u4f59u989d"></a>

**1) 请求地址**

> URL: {APIURL}/api/v1/player/balance

**2) 请求参数:**

| 参数名    | 类型            | 描述         |
| ------ | ------------- | ---------- |
| userid | string\[4-40] | 运营商的玩家唯一标识 |

* 示例：
  
  ```json
  {
  "userid": "testuser1",
  }
  ```

**请求示例代码**

```bash
curl --location --request POST 'https://{APIURL}/api/v1/player/balance' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "userid": "string"
}'
```

**3) 返回结果:**

| 参数名          | 类型      | 描述            |
| ------------ | ------- | ------------- |
| code         | integer | 返回状态码，0 表示成功  |
| error        | string  | 错误信息，成功时为空字符串 |
| data         | object  | 返回数据          |
| data.balance | float   | 玩家当前可用余额      |



* 玩家余额 43.45

* 示例：
  
  ```json
  {
  "code": 0,
  "error": "",
  "data": {
    "balance": 43.45,
    }
   }
  }
  ```
