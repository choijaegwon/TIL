# Google 로그인 구현하기   
~~~
flutter pub add google_sign_in
flutter pub add firebase_core
flutter pub add firebase_auth
~~~

## 공용 설정

<details>
<summary> 공용 설정</summary>

Firebase CLI 설치 및 로그인(firebase login 실행)
~~~
curl -sL https://firebase.tools | bash
~~~

로그인
~~~
firebase login
~~~  

프로젝트 리스트 보기
~~~
firebase projects:list
~~~ 
  
### 프로젝트로 이동
project cmd 창에
~~~
dart pub global activate flutterfire_cli
~~~
입력 후 
~~~
flutterfire configure --project=${파이어 베이스프로젝트명}
ex)
flutterfire configure --project=todo
~~~
입력  
프로젝트 선택
~~~
flutterfire configure 
~~~

### Friebase 홈페이지로 이동
Android들어가서 SHA-1 지문 등록  

## Google Console Cloud 설정 (지원 이메일 관련)

- 프로젝트 선택 → 새프로젝트
    - 프로젝트 이름
        - Firebase에 설정한 이름
- API 및 서비스
    - OAuth 동의 화면
        - 외부 클릭
    - 앱 이름
        - 동의를 요청하는 앱의 이름
    - 사용자 지원 이메일
        - 사용자가 동의 관련 질문을 위해 문의할 때 이용합니다.
    - 개발자 연락처 정보
        - 연락 받을 정보
- 범위 추가 및 삭제
    - 기본 Google 계정의 이메일 주소 확인
    - 개인정보(공개로 설정한 개인정보 포함) 보기
    - Google에서 내 개인 정보를 나와 연결

- 사용자 인증 정보
    - 사용자 인증 정보 만들기
        - **OAuth 클라이언트 ID 만들기**

<details>
<summary> iOS 설정</summary>

### iOS 설정

- Bundle ID 입력
    - Flutter → iOS → Open in Xcode → Runner → TARGETS → Signing & Capabilities → Bundle Identifiter
- URL 스키마 설정
    - Flutter → iOS → Open in Xcode → Runner  → TARGETS → Info → URL Types → URL Schemes 입력
        - 구글 **OAuth 에서 생성된 클라이언트 ID 입력**
    - 항상 항상 Secrets.xcconfig 파일을 생성해서 따로 공유 해줘야 한다.
    
    project → ios → Secrets.xcconfig
    
    ~~~
    FlutterGoogleLoginKey=com.googleusercontent.apps.1234214-lhkklhgbf2uvgwemm2fovdo1o343tu6 // 추가
    ~~~
    
    project → ios → .gitignore
    
    ~~~
    Secrets.xcconfig // 추가
    ~~~
    
    project → ios → Flutter → Debug.xcconfig
    
    project → ios → Flutter → Release.xcconfig
    
    ~~~
    #include "Secrets.xcconfig" // 추가
    ~~~
    
    project → ios → Runner → Info.plist
    
    ~~~
    <key>CFBundleURLTypes</key>
    <array>
        <dict>
            <key>CFBundleTypeRole</key>
            <string>Editor</string>
            <key>CFBundleURLSchemes</key>
            <array>
                <string>$(FlutterGoogleLoginKey)</string>
            </array>
        </dict>
    </array>
    ~~~
    
- plist 다운
    - GoogleService-Info.plist 파일명 변경
    - Flutter → iOS → Runner 위치에 넣기

</details>
            
<details>
<summary> AOS 설정</summary>


### AOS 설정

- 패키지 이름
    - Flutter → android → app → build.gradle
        - namespace 확인
- SHA-1 인증서 디지털 지문
    
    ~~~
    cd
    .anroid/
    keytool -list -v -keystore debug.keystore 
    ~~~
    
    비밀번호: andorid
    
    SHA1 복사 → 디지털 지문에 붙여넣기 → 저장
    
- JSON 다운
    - google-service.json 파일명 변경
        - Flutter → android → app 위치에 넣기
- project → android → build.gradle
    - 변경
        
        ~~~
        classpath 'com.google.gms:google-services:4.3.10’
        -> 
        classpath 'com.google.gms:google-services:4.3.14’
        ~~~

</details>  


### main.dart
~~~
WidgetsFlutterBinding.ensureInitialized();
await Firebase.initializeApp(
    options: DefaultFirebaseOptions.currentPlatform,
);
~~~

</details>

## 사용 코드

<details>
<summary> 사용 코드 </summary>  

~~~

// ----------------------------------------------------------------
// 구글 로그인
// ----------------------------------------------------------------

  /// 구글 로그인
  Future<void> signInWithGoogle() async {
    try {
      GoogleSignInAccount googleSignInAccount = await _getGoogleSignInAccount();
      String userId = await _getGoogleUserId(googleSignInAccount);
      String idToken = await _getGoogleIdToken(googleSignInAccount);
    } on Error {
      rethrow;
    }
  }

  /// 구글 계정 로그인
  Future<GoogleSignInAccount> _getGoogleSignInAccount() async {
    try {
      GoogleSignInAccount? result = await GoogleSignIn().signIn();
      return result!;
    } on Error {
      rethrow;
    }
  }

  /// userID 받아오기
  Future<String> _getGoogleUserId(
      GoogleSignInAccount googleSignInAccount) async {
    try {
      return googleSignInAccount.id;
    } on Error {
      rethrow;
    }
  }

  /// idToken 받아오기
  Future<String> _getGoogleIdToken(
      GoogleSignInAccount googleSignInAccount) async {
    try {
      GoogleSignInAuthentication googleSignInAuthentication =
          await googleSignInAccount.authentication;
      return googleSignInAuthentication.idToken!;
    } on Error {
      rethrow;
    }
  }

~~~

</details>


## idToken얻는게 iOS는 되는데 AOS는 안될때

<details>
<summary> idToken얻는게 iOS는 되는데 AOS는 안될때</summary>

(Firebase `GoogleSignIn` 없이 사용)  
(만약 Firebase를 사용한다면 clientId: Platform.isAndroid ? ApiKeys.androidGoogleLogin : null 부분을 지워줘야한다.)

### 1. Google Cloud 콘솔에서 구성되지 않은 빈 웹 OAuth 토큰 자격 증명을 만듭니다( **실제로 웹 클라이언트를 사용하지 않는 경우에도** 이 작업을 수행 ).

### 2. 웹 OAuth `clientId` 복사

### 3. api_keys.dart 파일생성

~~~
class ApiKeys {
  static const String androidGoogleLogin = clientId;
}
~~~

### 4. .gitignore

~~~
# APIKEY 숨기기
api_keys.dart
~~~

~~~
/// 구글 로그인
Future<void> signInWithGoogle() async {
  await GoogleSignIn().signOut();
  try {
    final GoogleSignInAccount? googleSignInAccount = await GoogleSignIn(
      clientId: Platform.isAndroid ? ApiKeys.androidGoogleLogin : null,
    ).signIn();
    final GoogleSignInAuthentication? googleSignInAuthentication =
        await googleSignInAccount?.authentication;
    String? token = googleSignInAuthentication?.idToken;

    if (token == null || googleSignInAccount == null) {
      throw ErrorDescription('GoogleLogin failed');
    }

    String? userId = googleSignInAccount.id;
  } on DioException {
    rethrow;
  }
}
~~~

</details>

# Reference
https://github.com/flutter/flutter/issues/20903#issuecomment-1433172720   
https://github.com/flutter/flutter/issues/20903   
https://console.cloud.google.com/apis/credentials?hl=ko&project=imposing-vista-288513   
