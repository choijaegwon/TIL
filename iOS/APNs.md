# APNs
- Apple Push Notification service의 약자
- Apple에서 만든 알람 서비스 플랫폼

## 생겨난 이유

애플이   
Server -> App 으로 바로 통신 못하고  
Server -> APNs -> App 으로 통신하도록 만들어서 생긴 것이다.

## 동작 원리

### 필수 사전 동작
1. App이 APNs에게 Device Token 요청
2. APNs가 App에게 Device Token 을 알려준다.
3. App이 Push Server에게 Device Token을 보내준다.  

### 통신을 위한 동작
1. Push Server는 Push를 보내고 싶을때, APNs에게 Device Token와 데이터를 보낸다.  
- Device Token + 데이터
- 이때 APNs와 Push Server는 TLS 통신이용
2. APNs는 해당 Device Token으로 데이터를 전송
3. App이름으로 Device에 푸쉬 알람이 뜬다.  

### 푸쉬알람의 데이터 형식
Push Server는 APNs에게
~~~
{
    "aps":
    {
        "alert": "안녕하세요",
        "sound" "default"
    }
}
~~~
이런 형태로 데이터를 보내줘야 한다.  

# Reference
https://babbab2.tistory.com/58  
