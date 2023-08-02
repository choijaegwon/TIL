# API통신 테스트

# 사용 Extention
- [REST Client](https://marketplace.visualstudio.com/items?itemName=humao.rest-client)

## ExCode
~~~
@hostname = '${서버 주소}'
@token = '${토큰값}'


### 회원 삭제 
DELETE https://{{hostname}}/api/user HTTP/1.1
content-type: application/json
Authorization: Bearer {{token}}

### 회원 정보 삭제
DELETE https://{{hostname}}/api/user/info HTTP/1.1
content-type: application/json
Authorization: Bearer {{token}}
~~~

# Reference
https://marketplace.visualstudio.com/items?itemName=humao.rest-client   