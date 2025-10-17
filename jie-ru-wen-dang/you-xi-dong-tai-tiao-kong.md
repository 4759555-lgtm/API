# 游戏动态调控

## 1) 请求地址

> URL: {APIURL}/api/v1/game/monitor

## 2) 请求参数

| 参数名                        | 类型        | 描述                                                                                                                                                                                                                                                                                                        |
| -------------------------- | --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| MoniterType                | int       | 监控类型，值为`0`时为`机台监控`值为`1`时为`个人监控`                                                                                                                                                                                                                                                                           |
| IsMoniter                  | int       | 监控的开启状态，值为`0`时为`关闭`值为`1`时为`开启`                                                                                                                                                                                                                                                                            |
| MoniterNewbieNum           | int       | 新玩家游戏局数                                                                                                                                                                                                                                                                                                   |
| MoniterRTPErrorValue       | int       | 玩家RTP误差范围                                                                                                                                                                                                                                                                                                 |
| MoniterNumCycle            | int       | 游戏内统计数据周期                                                                                                                                                                                                                                                                                                 |
| MoniterAddRTPRangeValue    | \[]object | <p>增加RTP范围，玩家RTP低于配置值时，有概率使玩家强制中奖。玩家RTP是指玩家在对应的机台的终生RTP。列表中的每一个object代表一个<code>挡位</code>，其中包含两个值<code>NewbieValue</code>,<code>NotNewbieValue</code>。<br><code>NewbieValue</code>为<code>int</code>类型，表示新手玩家RTP进行游戏调控的触发概率。<br><code>NotNewbieValue</code> 为<code>int</code>类型，表示非新手玩家RTP进行游戏调控的触发概率。</p>  |
| MoniterReduceRTPRangeValue | \[]object | <p>减少RTP范围，玩家RTP高于配置值时，有概率使玩家强制不中奖。玩家RTP是指玩家在对应的机台的终生RTP。列表中的每一个object代表一个<code>挡位</code>，其中包含两个值<code>NewbieValue</code>,<code>NotNewbieValue</code>。<br><code>NewbieValue</code>为<code>int</code>类型，表示新手玩家RTP进行游戏调控的触发概率。<br><code>NotNewbieValue</code> 为<code>int</code>类型，表示非新手玩家RTP进行游戏调控的触发概率。</p> |

* 示例：

```json
{
    "MoniterType": 0,
    "IsMoniter": 1,
    "MoniterNewbieNum": 50,
    "MoniterRTPErrorValue": 5,
    "MoniterNumCycle": 5,
    "MoniterAddRTPRangeValue": [{
        "NewbieValue": 0,
        "NotNewbieValue": 0
    }, {
        "NewbieValue": 4,
        "NotNewbieValue": 4
    }, {
        "NewbieValue": 8,
        "NotNewbieValue": 8
    }, {
        "NewbieValue": 12,
        "NotNewbieValue": 12
    }],
    "MoniterReduceRTPRangeValue": [{
        "NewbieValue": 0,
        "NotNewbieValue": 1
    }, {
        "NewbieValue": 5,
        "NotNewbieValue": 5
    }, {
        "NewbieValue": 10,
        "NotNewbieValue": 10
    }, {
        "NewbieValue": 15,
        "NotNewbieValue": 15
    }, {
        "NewbieValue": 20,
        "NotNewbieValue": 20
    }]
}
```

## 3) 返回结果

code为0为正常返回

* 示例：

```json
{
    "code": 0,
    "error": "",
    "data": {}
}
```
