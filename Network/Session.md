# Session
- 비밀번호 등 클라이언트의 민감한 인증 정보를 브라우저가 아닌 서버 측에 저장하고 관리
- Key-Value 형식의 객체로 구성

## 섹션 객체의 형태
---

<img width="392" alt="image" src="https://user-images.githubusercontent.com/68246962/235292653-bea36e15-f9ae-4c2b-9939-ac7c956b0d12.png">  


## 인증 방식
---

<img width="602" alt="image" src="https://user-images.githubusercontent.com/68246962/235292691-f303f6c4-bc86-4391-a1d4-355886c36719.png">   

1. 유저가 웹사이트에서 로그인하면 세션이 서버 메모리(혹은 데이터베이스) 상에 저장된다.이때, 세션을 식별하기 위한 Session Id를 기준으로 정보를 저장한다.
2. 서버에서 브라우저에 쿠키에다가 Session Id를 저장한다.
3. 쿠키에 정보가 담겨있기 때문에 브라우저는 해당 사이트에 대한 모든 Request에 Session Id를 쿠키에 담아 전송한다.
4. 서버는 클라이언트가 보낸 Session Id 와 서버 메모리로 관리하고 있는 Session Id를 비교하여 인증을 수행한다.

## 장점
---
- 보안 유지
- 큰 허용 용량
- 네트워크 부하가 거의 없다.

## 단점
---

- 해커가 SessionID를 탈취하면 클라이언트인척 위장할 수 있다. 
- 서버에 데이터를 저장하므로 세션 양이 많아질 수록 서버에 부하가 심해진다. 

# Reference
https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-JWTjson-web-token-%EB%9E%80-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC#token_%EC%9D%B8%EC%A6%9D_%EB%B0%A9%EC%8B%9D  