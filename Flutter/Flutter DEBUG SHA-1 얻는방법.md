# Flutter DEBUG SHA-1 얻는방법

## 터미널
~~~
..
cd .android 로 이동
~~~
~~~
keytool -list -v -keystore debug.keystore
~~~
입력후 비밀번호 android 를 입력하면 SHA-1을 얻을 수 있다.

## keytool 오류 발생 시
~~~
keytool 오류: java.io.IOException: Integrity check failed: java.security.NoSuchAlgorithmException: Algorithm HmacPBESHA256 not available 
~~~
터미널에
~~~
flutter doctor -v
~~~
입력후
~~~
Android toolchain의 Java binary at: /Applications/Android Studio.app/Contents/jbr/Contents/Home/bin/java
~~~
경로 확인 후 터미널에
~~~
cd ~
vi .zshrc
~~~
i 눌러 편집 후
~~~
export JAVA_HOME="/Applications/Android Studio.app/Contents/jre/jdk/Contents/Home"
~~~
뒤에 ”**/bin/java**” 빼고 경로 입력  wq!로 저장후 나온후
~~~
source ~/.zshrc
~~~
변경 사항 적용 다시 프로젝트 터미널로 돌아가서
~~~
flutter clean
flutter build appbundle
~~~
실행 후
~~~
..
cd .android 로 이동
keytool -list -v -keystore debug.keystore
~~~
입력   
비밀번호 → android 입력하면  
디버그용 SHA1을 얻을 수 있다.  

# Reference
https://stackoverflow.com/questions/67631927/error-building-aab-flutter-android-integrity-check-failed-java-security-n   
의 7번째 답변