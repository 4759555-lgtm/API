# 关闭玩家终身限制

## 1) 请求地址

> URL: {APIURL}/api/v1/player/cancelLifetimeControl

## 2) 请求参数

| 参数名  | 类型        | 描述                                              |
| ---- | --------- | ----------------------------------------------- |
| Uids | \[]string | 运营商的玩家唯一标识，可设置多个玩家（最少设置`1`个，最多可设置`100`个，否则将会报错） |

* 示例：

```json
{
	"Uids": ["123-DemoUser","456-DemoUser","789-DemoUser"],
}
```

## 3) 返回结果

| 参数名          | 类型        | 描述                  |
| ------------ | --------- | ------------------- |
| NotExistUids | \[]string | 运营商的玩家唯一标识，不存在的玩家id |

* 示例：

```json
{
    "code": 0,
    "error": "",
    "data": {
        "NotExistUids": [
            "123-DemoUser",
            "456-DemoUser",
            "789-DemoUser"
        ]
    }
}
```
