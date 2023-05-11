# Cookie
- Key-Value 형식의 문자열
- 이름, 값, 만료일, 경로 정보로 구성
- 클라이언트의 브라우저에 설치되는 작은 기록 정보 파일

## 인증 방식
---

<img width="778" alt="Untitled" src="https://user-images.githubusercontent.com/68246962/235292366-1025ef0c-64e9-4ff5-8140-9bb23278477b.png">  
1. 브라우저(클라이언트)가 서버에 요청(접속)을 보낸다.  
2. 서버는 클라이언트의 요청에 대한 응답을 작성할 때, 클라이언트 측에 저장하고 싶은 정보를 응답 헤더의 Set-Cookie에 담는다.  
3. 이후 해당 클라이언트는 요청을 보낼 때마다, 매번 저장된 쿠키를 요청 헤더의 Cookie에 담아 보낸다.서버는 쿠키에 담긴 정보를 바탕으로 해당 요청의 클라이언트가 누군지 식별하거나 정보를 바탕으로 추천 광고를 띄우거나 한다.  

## 장점
---

- 서버의 저장공간 절약

## 단점
---

- 보안에 취약
- 용량 제한
- 브라우저간 공유 불가능
- 네트워크에 부하가 심해짐

# Reference
https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-JWTjson-web-token-%EB%9E%80-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC#token_%EC%9D%B8%EC%A6%9D_%EB%B0%A9%EC%8B%9D  
https://brunch.co.kr/@jinyoungchoi95/1  