# build_runner

code generator이기에 dev_dependencies에 추가해줘야한다.

## 사용 코드
- 빌드 러너가 한 번만 작동되고 종료됨.
~~~
flutter pub run build_runner build
~~~

- 빌드 러너를 계속 작동시켜 파일이 변경될 때를 계속 수신하고 있음.
~~~
flutter pub run build_runner watch --delete-conflicting-outputs
~~~