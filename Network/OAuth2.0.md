# OAuth2.0
- 인증을 위한 개방형 표준 프로토콜
- 구글, 페이스북 등 외부 소셜 계정을 기반으로 간편하게 인증하는 기능

## 제공자
- 구글
- 페이스북
- 카카오
- 네이버

## 핵심 용어
---
- Authentication: 인증, 접근 자격이 있는지 검증하는 단계
- Authorization: 인가, 자원에 접근할 권한을 부여하는것, 인가가 완료되면 리소스 접근 권한이 담긴 AccessToken을 클라이언트에게 부여 
- AccessToken: 리소스 서버에게서 리소스 소유자의 보호된 자원을 획득할 때 사용되는 만료 기간이 있는 Token
- RefreshToken: AccessToken만료시 이를 갱신하기 위한 용도

## 역할 4가지
---
- ResourceOwner: 리소스 소유자 또는 사용자. 보호된 자원에 접근할 수 있는 자격을 부여해 주는 주체. OAuth2 프로토콜 흐름에서 클라이언트를 인증(Authorize)하는 역할을 수행합니다. 인증이 완료되면 권한 획득 자격(Authorization Grant)을 클라이언트에게 부여 개념적으로는 리소스 소유자가 자격을 부여하는 것이지만 일반적으로 권한 서버가 리소스 소유자와 클라이언트 사이에서 중개 역할을 수행하게 됩니다.
- Client: 보호된 자원을 사용하려고 접근 요청을 하는 애플리케이션
- ResourceServer: 사용자의 보호된 자원을 호스팅하는 서버
- AuthorizationServer: 권한 서버. 인증/인가를 수행하는 서버로 클라이언트의 접근 자격을 확인하고 Access Token을 발급하여 권한을 부여하는 역할을 수행

## 시퀀스 다이어그램 플로우
---

<img width="755" alt="image" src="https://user-images.githubusercontent.com/68246962/235296360-78a1abf3-c6ec-4805-967d-2266b13cdaf1.png">  

## AuthorizationCodeGrant(권한 부여 승인 코드 방식)
---

- 간편 로그인 기능에서 사용되는 방식
- 권한 부여 승인을 위해 자체 생성한 Authorization Code를 전달하는 방식으로 많이 쓰이고 기본이 되는 방식
- 클라이언트가 사용자를 대신하여 특정 자원에 접근을 요청할 때 사용되는 방식
- RefreshToken 사용 가능  

<img width="615" alt="image" src="https://user-images.githubusercontent.com/68246962/235296320-1255bdd7-213e-483a-b24b-f84df3698307.png">  

### 동작 방식
1. request에 포함된 redirect_url로 Authorization Code를 전달  
2. Authorization Code는 Authorization Server를 통해 Access Token으로 교환  
3. Access Token을 사용하여 Reource Server에 접근  

## ImplicitGrant(암묵적 승인 방식)
---

- 자격증명을 안정하게 저장하기 힘든 클라이언트에게 최적화된 방식
- 권한 부여 승인 코드 없이 바로 AccessToken 바급
- RefreshToken 사용 불가
- Access Token이 URL로 전달 된다는 단점  

<img width="622" alt="image" src="https://user-images.githubusercontent.com/68246962/235296466-58cdb96d-91f6-4013-bc59-4c591dbd7f28.png">  

1. 권한 부여 승인 요청 시 response_type을 token으로 설정하여 요청
2. 클라이언트는 권한 서버에서 제공하는 로그인 페이지를 브라우저를 띄워 출력
3. 로그인이 완료되면 권한 서버는 Authorization Code가 아닌 Access Token를 redirect_url로 바로 전달  

## ResourceOwnerPasswordCredentialsGrant(자원 소유자 자격증명 승인 방식)
---

- username, password로 AccessToken을 받는 방식  
- 클라이언트가 자신의 서비스에서 제공하는 어플리케이션일 경우에만 사용하는 방식
- RefreshToken 사용 가능  

<img width="609" alt="image" src="https://user-images.githubusercontent.com/68246962/235296729-9f4caa51-723a-40d4-a9ec-420946cca76f.png">  

## ClientCredentialsGrant(클라이언트 자격증명 승인 방식)
---

- 클라이언트의 자격증명만으로 AccessToken을 획득하는 방식
- 클라이언트 자신이 관리하는 리소스 혹은 권한 서버에 해당 클라이언트를 위한 제한된 리소스 접근 권한이 설정되어 있는 경우 사용
- 가장 간단한 방식
- 자격증명을 안전하게 보관할 수 있는 클라이언트에서만 사용
- RefreshToken 사용 불가  

<img width="474" alt="image" src="https://user-images.githubusercontent.com/68246962/235297106-d3d41c45-7adf-420e-8b51-215606d0bc7c.png">  


# Reference
https://blog.naver.com/mds_datasecurity/222182943542  
https://velog.io/@kimjaejung96/OAuth2.0-%EA%B0%9C%EB%85%90-%EB%B0%8F-%EC%9E%91%EB%8F%99%EB%B0%A9%EC%8B%9D  
