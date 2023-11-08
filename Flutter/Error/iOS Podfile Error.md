# iOS Podfile Error.md
플러터에서 iOS 기기를 실행했을때 발생

## Error code
~~~
[!] Automatically assigning platform `iOS` with version `11.0` on target `Runner` because no platform was specified.    
Please specify a platform for this target in your Podfile. See `https://guides.cocoapods.org/syntax/podfile.html#platform`.
~~~

## 해결방법
- project -> ios -> Podfile
맨위 #platform 주석제거
~~~
platform :iox, '11.0'
~~~

# Reference
https://blog.dglee.co.kr/34