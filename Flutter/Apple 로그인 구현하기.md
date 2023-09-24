# Apple 로그인 구현하기

~~~
flutter pub add sign_in_with_apple
~~~

## Apple 등록 및 전체적인 설정
https://developer.apple.com/account  
접속 후 로그인   
https://developer.apple.com/account/resources/certificates/list   

<details>
<summary> App ID 설정</summary>

- identifiers → + → 새로운 식별자 등록 (App)  
    - Description  
        - 알아볼 설명  
    - Bundle ID   
        - App의 번들 ID 입력  
    - Sign In With Apple 체크  
</details>

<details>
<summary> Keys 설정 </summary>

- Keys → + Create a key → 보기편한 KeyName 입력 → Sign in with Apple 클릭 → Configure 클릭 → 아까 등록한 App ID 선택 후 저장 후 등록 → Key 다운로드  
</details>

<details>
<summary> Service ID 설정</summary>

- Identifiers → + → Services IDs 체크 → Continue
    - Description
        - 설명
    - Identifier
        - App ID의 역순(권장사항)
        - ex) com.example.projectName ⇒ projectName.example.com
        - 난 추가로 -service를 붙였다
        - ex) projectName.example.com-service
- Countinue → Register
</details>

<details>
<summary> glitch 설정</summary>

- TEMAM_ID
    - identifiers → APP ID → 프로젝트 → **App ID**
- BUNDLE_ID
    - identifiers → APP ID  → 프로젝트 → **Bundle ID**
- SERVICE_ID
    - identifiers → SERVICE_ID → 프로젝트 → **Identifier**
- KEY_ID
    - Keys → 프로젝트 → **Key ID**
- KEY_CONTENTS
    - Keys → 프로젝트 → Keys 다운로드
    - finder → 편집기로 열기 → 한줄로 이어 붙이기
- ****ANDROID_PACKAGE_IDENTI****
    - Flutter → android → app → build.gradle → namespace
    - 안드로이드 패키지명
</details>

<details>
<summary> Service ID Redirect Url 설정</summary>

- identifiers → Service IDs → 프로젝트 명 → Configure
- **Primary App ID**
    - **프로젝트 명 클릭**
- **Domains and Subdomains**
    - [www.google.com](http://www.google.com)
    - 되는 url 넣어주기
- **Return URLs**
    - glitch 에서 설정한 url 뒤에 /callbacks/sign_in_with_apple 를 붙여주기

</details>

<details>
<summary> iOS 프로젝트</summary>

- project → ios → Open in Xcode
- Runner → TAGETS → Runner → Setting & Capabilites    

<img width="1524" alt="image" src="https://github.com/choijaegwon/choijaegwon.github.io/assets/68246962/ce9de729-f62a-49f6-b1e3-8d72711325ef">   

+ 누른후

![image](https://github.com/choijaegwon/choijaegwon.github.io/assets/68246962/2d9ee166-45b4-403b-9393-1cd5e7f2e223)  

Sign in with Apple 추가
</details>

## AOS 설정

<details>
<summary> AOS</summary>

- project → app → src → main → AndroidManifest.xml  
~~~
<activity
  android:name="com.aboutyou.dart_packages.sign_in_with_apple.SignInWithAppleCallback"
  android:exported="true">
     <intent-filter>
        <action android:name="android.intent.action.VIEW" />
        <category android:name="android.intent.category.DEFAULT" />
        <category android:name="android.intent.category.BROWSABLE" />
        <data android:scheme="signinwithapple" />
        <data android:path="callback" />
     </intent-filter>
</activity>
~~~

## 전체코드
<details>
<summary> 전체코드</summary>

~~~
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.study.social_login_app">
   <application
        android:label="social_login_app"
        android:name="${applicationName}"
        android:icon="@mipmap/ic_launcher">
        .
        .
        .
        <!-- 추가 -->
        <activity
          android:name="com.aboutyou.dart_packages.sign_in_with_apple.SignInWithAppleCallback"
          android:exported="true">
             <intent-filter>
                <action android:name="android.intent.action.VIEW" />
                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />

                <data android:scheme="signinwithapple" />
                <data android:path="callback" />
             </intent-filter>
        </activity>
        .
        .
        .
    </application>
</manifest>
~~~

</details>

## 사용 코드

~~~
// ----------------------------------------------------------------
// 애플 로그인
// ----------------------------------------------------------------

  /// 애플로그인
  Future<void> signInWithApple() async {
    try {
      final AuthorizationCredentialAppleID credential = await _getCredential();

      String identityToken = await _getAppleIdentityToken(credential);
      String userId = await _getAppleUserIdAOS(identityToken);
      String idToken = base64Encode(utf8.encode(identityToken));
    } on Error {
      rethrow;
    }
  }

  /// apple에 로그인
  Future<AuthorizationCredentialAppleID> _getCredential() async {
    try {
      return await SignInWithApple.getAppleIDCredential(
        scopes: [
          AppleIDAuthorizationScopes.email,
          AppleIDAuthorizationScopes.fullName,
        ],
        // TODO: AOS IOS 분기처리 필요 AOS만 아래 코드가 필요하다
        webAuthenticationOptions: WebAuthenticationOptions(
          clientId: 'com.popprika.popprikaBikeControllerFlutterApp-service',
          redirectUri: Uri.parse(
            ApiKeys.appleLoginRedirectUri,
          ),
        ),
      );
    } on Error {
      rethrow;
    }
  }

  Future<String> _getAppleIdentityToken(
      AuthorizationCredentialAppleID credential) async {
    try {
      return credential.identityToken!;
    } on Error {
      rethrow;
    }
  }

  Future<String> _getAppleUserIdAOS(String identityToken) async {
    try {
      List<String> jwt = identityToken.split('.');
      String payload = jwt[1];
      payload = base64.normalize(payload);

      final List<int> jsonData = base64.decode(payload);
      final userInfo = jsonDecode(utf8.decode(jsonData));
      return userInfo['sub'];
    } on Error {
      rethrow;
    }
  }
~~~

</details>
  
# Reference
https://pub.dev/packages/sign_in_with_apple   
https://dalgoodori.tistory.com/49   
