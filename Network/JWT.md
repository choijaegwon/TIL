# JWT
- Json Web Token의 약자
- 유저를 인증하고 식별하기 위한 토큰 기반 인증
- 클라이언트에 저장된다.
- 토큰 자체에 사용자의 권한 정보나 서비스를 사용하기 위한 정보가 포함되어있다.
- 사용자의 정보를 바꿀때 토큰을 재발급 받아야한다.
- 인증에 필요한 정보들을 암호화시킨 JSON 토큰
- Header, Payload, Signature 를 의미

## JWT 구조
---

<img width="961" alt="image" src="https://user-images.githubusercontent.com/68246962/235294290-77adb2e6-2f7a-4831-85a5-c974395645e2.png">  

![image](https://user-images.githubusercontent.com/68246962/235294342-b75722ec-2b31-4395-ad47-eeec0243ec6f.png)  
- Header: JWT 에서 사용할 타입과 해시 알고리즘의 종류가 담겨있다.  

![image](https://user-images.githubusercontent.com/68246962/235294368-6dda1954-1c98-4035-9bc6-fde4ce0953a3.png)  
- Payload: 서버에서 첨부한 사용자 권한 정보와 데이터가 담겨있다.    

![image](https://user-images.githubusercontent.com/68246962/235294390-cb66a99a-cd82-41f8-9918-624cdc9179ed.png)  
- Signature: Header, Payload 를 Base64 URL-safe Encode 를 한 이후 Header 에 명시된 해시함수를 적용하고, 개인키(Private Key)로 서명한 전자서명이 담겨있다.  

 ## 인증 방식
 ---

![image](https://user-images.githubusercontent.com/68246962/235294427-df071975-fe87-420b-890f-cbb0a51b4f57.png)  

## 장점
---

- Header와 Payload를 가지고 Signature를 생성하므로 데이터 위변조를 막을 수 있다.
- 인증 정보에 대한 별도의 저장소가 필요없다.   
- JWT는 토큰에 대한 기본 정보와 전달할 정보 및 토큰이 검증됬음을 증명하는 서명 등 필요한 모든 정보를 자체적으로 지니고 있다.
- 클라이언트 인증 정보를 저장하는 세션과 다르게, 가 되어 서버 확장성이 우수해질 수 있다. 서버는 무상태(StateLess)
- 토큰 기반으로 다른 로그인 시스템에 접근 및 권한 공유가 가능하다. (쿠키와 차이)
- OAuth의 경우 Facebook, Google 등 소셜 계정을 이용하여 다른 웹서비스에서도 로그인을 할 수 있다.
- 모바일 어플리케이션 환경에서도 잘 동작한다. (모바일은 세션 사용 불가능)

## 단점
--- 
- Self-contained : 토큰 자체에 정보를 담고 있으므로 양날의 검이 될 수 있다.
- 토큰 길이 : 토큰의 Payload에 3종류의 클레임을 저장하기 때문에, 정보가 많아질수록 토큰의 길이가 늘어나 네트워크에 부하를 줄 수 있다.
- Payload 인코딩 : payload 자체는 암호화 된 것이 아니라 BASE64로 인코딩 된 것이기 때문에, 중간에 Payload를 탈취하여 디코딩하면 데이터를 볼 수 있으므로, payload에 중요 데이터를 넣지 않아야 한다.
- Store Token : stateless 특징을 가지기 때문에, 토큰은 클라이언트 측에서 관리하고 저장한다. 때문에 토큰 자체를 탈취당하면 대처하기가 어렵게 된다.



# Reference
https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-JWTjson-web-token-%EB%9E%80-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC#token_%EC%9D%B8%EC%A6%9D_%EB%B0%A9%EC%8B%9D    