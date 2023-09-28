# shorebird(code push)

### 1. 터미널 열고 설치
~~~
curl --proto '=https' --tlsv1.2 https://raw.githubusercontent.com/shorebirdtech/install/main/install.sh -sSf | bash
~~~

~~~
vi ~/.zshrc
~~~
수정 모드 진입 후   
절대 경로 입력
~~~
export PATH="/Users/seven/.shorebird/bin:$PATH"
~~~

코드 적용(재실행)
~~~
source ~/.zshrc
~~~

### 2. 로그인
~~~
shorebird login
~~~ 
링크 누르기

### 3. Flutter 프로젝트에서 Shorebird를 초기화
~~~
shorebird init
~~~

### 4. 릴리즈 만들기

~~~
shorebird release android
~~~

### 5. 릴리스 설치
~~~
a. Install the generated apk on a device/emulator
b. Upload the generated aab to the Play Store
c. Use shorebird run to run the release on a connected device/emulator.
~~~

### 6. 코드 변경 후 아래 명령어 입력

~~~
shorebird patch android
~~~

### 앱 재실행


# Reference
https://console.shorebird.dev/login   
https://medium.com/@vovaklh20012/code-push-for-flutter-update-your-app-without-new-release-using-shorebird-d3575ba0a2c0   
https://dev.to/dev_toykam/shorebird-x-flutter-some-things-you-should-know-3n1m   
https://sweetcoding.tistory.com/224   
