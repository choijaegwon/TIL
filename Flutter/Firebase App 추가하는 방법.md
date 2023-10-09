# Firebase App 추가하는 방법

## Project Cmd
### pub 설치
~~~
flutter pub add firebase_core
~~~

### 프로젝트 생성후 Flutter 클릭
https://console.firebase.google.com/u/0/?hl=ko

## Cmd
### curl 설치
~~~
curl -sL https://firebase.tools | bash
~~~

### 파이어베이스 로그인
~~~
firebase login
~~~

### 목록가져오기  

~~~
firebase projects:list
~~~

## Project Cmd
~~~
dart pub global activate flutterfire_cli
~~~

~~~
flutterfire configure --project={프로젝트마다 다르다}
ex)  
flutterfire configure --project=todo-abcd
~~~

## 최신상태인지 확인
~~~
flutterfire configure
~~~

