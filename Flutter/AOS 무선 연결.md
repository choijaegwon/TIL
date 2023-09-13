# AOS 무선 연결

~~~
cd /Users/${user이름}/Library/Android/sdk/platform-tools
./adb devices
./adb tcpip 5555
./adb connect 와이파이주소:5555
~~~

- 연결할 디바이스를 찾기
~~~
./adb devices
~~~

- 5555로 포트번호 5555로 설정해주기
~~~
./adb tcpip
~~~

- 와이파이주소:5555 와이파이의 5555포트로 연결
~~~
./adb connect
~~~

# Reference
https://miaow-miaow.tistory.com/160  