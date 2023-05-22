# AppVersion&Build정보  
- iOS에서는 현재 사용자가 실행 중인 앱의 버전과 빌드 번호를 확인할 수 있다.
- 빌드 앱해서 스토어에 올리면 바이너리에는 적용 번들 정보를 보고 있다.
- 버전은 할 때마다 보이고 보통 xxx의 형태를 사용한다.
- 유사하게 버전과 빌드를 코드로 확인할 수 있다.

~~~
let version = Bundle.main.object(forInfoDictionaryKey: "CFBundleShortVersionString") as! String
let build = Bundle.main.object(forInfoDictionaryKey: kCFBundleVersionKey as String) as! String
~~~

# Reference
https://hongssup.tistory.com/134  