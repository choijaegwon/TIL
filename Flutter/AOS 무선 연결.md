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
./adb tcpip 5555
~~~
- 만약 연결 되어있는 디바이스가 많다면
~~~
./adb -s {디바이스} tcpip 5555
~~~

- 와이파이주소:5555 와이파이의 5555포트로 연결
~~~
./adb connect {wifi주소:5555}
~~~
- 만약 연결 되어있는 디바이스가 많다면
~~~
./adb -s {디바이스} connect {wifi주소:5555}
~~~

# Reference
https://miaow-miaow.tistory.com/160  
