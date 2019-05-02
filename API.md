# 个人信息

* 登陆 - `post`

  ```
  api/login
  ```

  Request 表单信息

  ```
  [
  	code: 登录时获取的 code
  ]
  ```

  向微信服务器获取**openid**和**session_key**

  Response 返回信息

  ```
  [
  	token: "聚宽的token"
  	openid：用户唯一标识	
  ]
  ```

  

  ![login](./images/login.png)

* 获取自选股信息 - `get`

  ```
  api/users/{username}
  ```

* 增加/删除自选股信息 - `post`

  ```
  api/stocks
  ```

  表单信息：

  ```
  [
      UserID: string
      StockID: string
  ]
  ```

# 咨询信息
* 分页获取咨询信息 - `get`
  ```
  api/news
  ```

* 信息来源：今日经济类新闻

* Resonse

  ```
  [
  	[
  		title: string
  		time: string
  		detail: string
  	],
  	...
  
  ]
  ```

  

# 信息获取

