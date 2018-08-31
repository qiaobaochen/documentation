# Lantern Fish 接口说明

基于Python Flask 的 Restful API

> 详细文档 [Wiki](https://github.com/lantern-fish/documentation/wiki)

## 鉴权说明

采用JWT, 推荐使用 [Flask-JWT](https://pythonhosted.org/Flask-JWT/#flask-jwt) 

**To get a token make a request to the auth resource:**

```
POST /auth HTTP/1.1
Host: localhost:5000
Content-Type: application/json

{
    "username": "joe",
    "password": "pass"
}
```

**The response should look similar to:**

```
HTTP/1.1 200 OK
Content-Type: application/json

{
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZGVudGl0eSI6MSwiaWF0IjoxNDQ0OTE3NjQwLCJuYmYiOjE0NDQ5MTc2NDAsImV4cCI6MTQ0NDkxNzk0MH0.KPmI6WSjRjlpzecPvs3q_T3cJQvAgJvaQAPtk1abC_E"
}
```

**This token can then be used to make requests against protected endpoints:**

```
GET /protected HTTP/1.1
Authorization: JWT eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZGVudGl0eSI6MSwiaWF0IjoxNDQ0OTE3NjQwLCJuYmYiOjE0NDQ5MTc2NDAsImV4cCI6MTQ0NDkxNzk0MH0.KPmI6WSjRjlpzecPvs3q_T3cJQvAgJvaQAPtk1abC_E
```

### 其余接口通用格式

**调用成功**

```json
{
    "success":true,
    "data":{
        // 返回的数据
    }
}
```

**调用失败**

```json
{
    "success":false,
    "error":"权限错误" //返回错误原因, 因为要显示在页面上, 所以规范写
}
```




