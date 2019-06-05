# API

---
---

## 用户相关

### 登陆 - `post`

```
api/login
```

`Request` -  `application/json`

```
[
  code: string 登录时获取的code
]
```

> 三方服务器向微信服务器获取**openid**和**session_key**

`Response` 

```
[
  token: string 聚宽的token
  openid：string 用户唯一标识
  isVip: bool 是否是VIP
  msg: string 报错信息
  stocks: [
    code string 股票代码,
    ......
  ] json 用户收藏的股票
]
```



![login](./images/login.png)

### 获取自选股信息 - `get`

```
api/stocks/{userid}
```

`Response:`

```
[
  userId: string userid
  stocks: [
    code string 股票代码,
    ......
  ]
  msg: string 报错信息
]
```
  
### Vip校验 - `post`

```
api/user/vip
```

`Request`  -  `application/json`

```
[
  userId: string 用户唯一标识
  vipCode: string vip校验码
]
```

`Response`

```
[
  userId: string 用户唯一标识
  status: bool 是否成功认证
  msg: string 报错信息
]
```

---

## 资讯信息

### 分页获取咨询信息 - `get`
```
api/news?from=[0-9]+&to=[0-9]+
```

信息来源：今日经济类新闻

Resonse

```
[
  from: int 起始 
  to:   int 结束
  msg:  string 报错信息
  data：[
    [
      title:  string  标题
      time:   string  时间
      detail: string  具体内容
    ],
    ...
  ]
]
```
---

## 股票相关

### 增加/删除自选股信息 - `post`

```
增加：api/stocks/add
删除：api/stocks/remove 
```

`Request` -  `application/json` 

```
[
  userId: string 用户唯一标识
  stockCode: string 股票代码
]
```
`Response:`
```
[
  userId: string 用户唯一标识
  stocks: [
    code string 股票代码,
    ......
  ]
  msg: string 报错信息
]
```

### 智能选股信息获取 -  `post`
> vip用户专享
```
api/stocks/recommend
```
`Request`  -  `application/json`

```
[
  userId: string 用户唯一标识
]
```
`Response`
```
[
  data: {
    strategy: {
      successRate:  int     综合成功率
      operation:    string  操作类型
      usage:        string  核心用法
      stocks: [
        {
          last_close    string  昨收
          today_open    string  今开
          last_price    string  最新价
          change        string  变动
          change_rate   string  变动比例
          code          string  股票代码
          date          string  日期
          name          string  股票名称
          strategy      string  策略名称
        },
        ......
      ] 策略智能推荐的股票
    } 策略,
    ...
  }
  msg: string 报错信息
]
```

### 获取某支股票近日的评论 - `get`

```
api/stock/{stockCode}/comment
```

信息来源：东方财富股吧、雪球网、新浪财经

`Resonse`

```
[
  msg:    string  报错信息
  code:   string  股票代码
  score:  int     股票评分
  data：[
    [
      title:  string  标题
      time:   string  时间
      detail: string  具体内容
      author: string  作者
      emotion: string 情感分析结果
    ],
    ...
  ] 评论
]
```




