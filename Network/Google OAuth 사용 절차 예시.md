# Google OAuth 사용 절차 예시

1. **구글 Cloud API 및 서비스 콘솔 내에서 프로젝트 생성**  
https://console.cloud.google.com/projectselector2/apis?pli=1  

2. **사용할 API 선택**  

3. **사용자 인증 정보 란에서 OAuth 2.0 클라이언트 ID 생성** (SHA-1 인증서 디지털 지문 필요)  
- 개발시에는 디버그 키를 사용해야함 (keytool 명령어 이용하여 debug.keystore 추출)
- 심사시에는 릴리즈 키를 사용해야함
- 심사 후 마켓 버전에서 OAuth창이 잘 뜨지 않는 경우  
    1. `구글 플레이 스토어 콘솔(play.google.com/console)의 해당 앱 내`에서
출시 → 설정 → 앱 무결성 → 앱 서명 → **표기된 SHA-1 인증서 지문** 을 복사
    2. `구글 Cloud API 및 서비스 콘솔 내`에서
해당 프로젝트 → 사용자 인증 정보 → OAuth 2.0 클라이언트 ID 생성 
(위의 a단계 에서 복사한 SHA-1 인증서 지문 사용)

4. **OAuth 동의 화면 설정 및 심사**
    
    <aside>
    💡 해당 심사는 앱에 대한 심사와는 별도의 심사임을 명심해야할 것 
    또한, 구글 문서상에서는 4~5주 이상 소요된다고 표기되어있으며 다른 개발자의 글에선 최대 2달까지 소요된다고함
    
    </aside>
    
    - 설정시 필요한 정보
        - 서비스 아이콘
        - 서비스 홈페이지 URL
            - Google API를 사용하는 서비스에 대한 단독 홈페이지
            - 해당 서비스가 어떤 서비스인지에 대한 내용이 홈페이지에 모두 포함되어 있어야함
            - 개인정보처리방침이 포함되어 있어야함
        - 개인정보처리방침 URL
            - 서비스 홈페이지 내에 있는 개인정보처리방침과 동일한 URL이어야함
            - 개인정보처리방침 내에 GoogleFit을 사용한다는 내용이 명시되어 있어야함
        - Google Search Console ([링크](https://search.google.com/search-console/about)) 를 통해 등록/인증한 도메인
            - 서비스 홈페이지 / 개인정보처리방침 URL에 포함된 도메인은 모두 인증 받아야함
            - 노션페이지 사용 불가 → 노션 도메인을 본인 소유라고 인증받아야하므로.
        - 민감한 범위의 API사용 부분에 대해 어떤 방식으로 사용되는지 설명 작성
        - 앱내에서 사용하려는 Google API가 어떻게 사용되는지 녹화한 영상
            - 영상을 찍어 Youtube에 업로드하고 URL 공유
            - OAuth 인증페이지가 영문으로 보이도록 해야함

# Reference
https://console.cloud.google.com/projectselector2/apis  