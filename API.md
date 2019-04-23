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

# 信息获取

