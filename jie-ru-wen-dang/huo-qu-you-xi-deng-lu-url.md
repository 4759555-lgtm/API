# 获取游戏登录 URL

## 1) 请求地址

> URL: {APIURL}/api/v1/game/launch

## 2) 请求参数:

| 参数名      | 类型            | 描述              |
| -------- | ------------- | --------------- |
| UserID   | string\[4-40] | 运营商玩家唯一标识       |
| GameID   | string        | 游戏 ID           |
| Language | string        | 语言设定 th, en ... |

* 示例：

```json
{
  "UserID": "operator_user_abcd",
  "GameID": "pg_98",
  "Language": "th"
}
```

## 3) 返回结果:

| 参数名 | 类型     | 描述      |
| --- | ------ | ------- |
| Url | string | 游戏登录URL |

* 示例：

```json
{
  "error": "",
  "data": {
    "Url": "https://popapi.cc/pg_98/index.html?l=th&t=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxODcsIlMiOjEwMDIsIkQiOiJYaW5nWXVuWGlhbmcifQ.9td-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxmw"
   }
}
```
