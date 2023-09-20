# Flutter SHA-1 생성하는 방법

## 키 생성
~~~
keytool -genkey -v -keystore ~/key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias key -storetype JKS
~~~
위 명령어를 설정하면 /Users/사용자이름 위치에 key.jks파일이 생성된다.(/Users/사용자이름/key.jks) 터미널에서 ..로 돌아가서

## 키 추출
cd..
~~~
keytool -list -v -keystore key.jks
~~~
를 작성하면 인증서(SHA-1)가 나온다.

### ※ 위에서 key.jks 로 생성을 하여서 key.jks파일로 찾아줘야한다.

# Reference
https://velog.io/@terman/Flutter-%EC%95%B1-%EC%84%9C%EB%AA%85-key.jks-%EC%9D%BD%EA%B8%B0-%EC%8B%A4%ED%8C%A8Failed-to-read-key-key-from-store-androidappkey.jks-Integrity-check-failed-java.security.NoSuchAlgorithmException-Algorithm-HmacPBESHA256-not-available    
https://bora-dev.tistory.com/11   
https://prince-mint.tistory.com/11   