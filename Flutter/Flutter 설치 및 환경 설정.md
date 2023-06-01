# Flutter 설치 및 환경 설정

## 다운로드 
1. 파일설치
2. 원하는 위치에 알집 해제
3. flutter 경로에 도구 추가

~~~
export PATH="$PATH:`pwd`/flutter/bin"
~~~
여기서  
~~~
`pwd`
~~~
란 폴더 경로 이다.

4. 설치 확인  

~~~
flutter doctor
~~~
성공시   
<img width="574" alt="Untitled" src="https://github.com/choijaegwon/choijaegwon.github.io/assets/68246962/f76dadb8-7980-4a05-99ac-6709dbca8b94">  

화면을 볼 수 있다.
하지만 이렇게 환경 변수를 설정 해 두면 이 폴더에서만 flutter 명령어를 사용할 수 있다.  
따라서 어디에서든 명령어를 실행할 수 있게 해야하는데,  
1. 터미널을 열기.  

~~~
vi ~/.zshrc
~~~  

2. 편집모드 변경  
- 예시(/Users/jaekwonchoi/Downloads/study/)는 파일 경로이다.  

~~~
export PATH="$PATH:/Users/jaekwonchoi/Downloads/study/flutter/bin"
~~~
  
3. 재실행  

~~~
source ~/.zshrc
~~~ 

4. 확인  

~~~
flutter doctor
~~~

## Xcode 설치
1. 홈페이지 가서 최신 버전 다운
2. 드래그로 설치
3. 설정해주기
~~~
sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer
sudo xcodebuild -runFirstLaunch
~~~

4. CocoaPad 설치  
~~~
sudo gem install cocoapods
~~~

5. 설치 확인  

~~~
pod --version
~~~

## AndroidStudio 설치
1. 파일설치
2. 알집해제
3. 파일 경로 설정  

~~~
flutter config --android-studio-dir="파일경로 넣어주기 + 파일명"
~~~

4. 안드로이드 SDK 파일 확인하기  

<img width="783" alt="Untitled" src="https://github.com/choijaegwon/choijaegwon.github.io/assets/68246962/2bec977d-df06-4576-9b94-5e304afd0c4c">  

- SDK Manager 클릭  

<img width="967" alt="Untitled" src="https://github.com/choijaegwon/choijaegwon.github.io/assets/68246962/851ec975-b747-4560-a0fc-6bbdfeadd5f3">  

- SDK Tools 클릭
- Android SDK Command-line Tools (latest) 체크 후 Apply를 진행 후  

~~~
flutter doctor --android-licenses
~~~
실행, 후 수락(y + Enter)


# Reference
https://docs.flutter.dev/get-started/install/macos#get-sdk   
https://developer.apple.com/xcode/  
https://developer.android.com/studio  
https://stackoverflow.com/questions/68236007/i-am-getting-error-cmdline-tools-component-is-missing-after-installing-flutter  
