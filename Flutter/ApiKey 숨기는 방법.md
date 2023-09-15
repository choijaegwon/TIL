# ApiKey 숨기는 방법

## AOS
android → local.properties 
~~~
원하는 변수명 = apiKeyString값

ex)

flutter.kakao.nativeKey = kakao어쩌구저쩌구apikey
~~~

android → app → build.gradle  
~~~
def 원하는 변수명 = localProperties.getProperty('위에서 설정한 변수명')
if (원하는 변수명 == null ) {
  // 예외 처리
}

ex)

def flutterKakaoNativeKey = localProperties.getProperty('flutter.kakao.nativeKey')
if (flutterKakaoNativeKey == null) {
    log('error: kakaoApi');
}
~~~

~~~
defaultConfig {
	manifestPlaceholders["위에서 설정한 변수명"] = 위에서 설정한 변수명
}

ex)

defaultConfig {
	manifestPlaceholders["flutterKakaoNativeKey"] = flutterKakaoNativeKey
}
~~~

android → app → src → main → AndroidManifest.xml
~~~
<data android:scheme='${위에서 설정한 변수명}' android:host="oauth"/>

ex)

<data android:scheme='${flutterKakaoNativeKey}' android:host="oauth"/>
~~~  

## iOS

ios → Flutter → Debug.xcconfig

~~~
KAKAO_API_KEY = kakao"${api키}"

ex)

KAKAO_API_KEY = kakao1231sdlmdlmsdflmsdflmsdfml
~~~

ios → Flutter → Release.xcconfig

~~~
KAKAO_API_KEY = kakao"${api키}"

ex)

KAKAO_API_KEY = kakao1231sdlmdlmsdflmsdflmsdfml
~~~

ios → Runner → Info.plist
~~~
<key>CFBundleURLTypes</key>
	<array>
		<dict>
			<key>CFBundleTypeRole</key>
			<string>Editor</string>
			<key>CFBundleURLSchemes</key>
			<array>
				<string>${위에서 설정한 변수}</string>
			</array>
		</dict>
	</array>

ex)

<key>CFBundleURLTypes</key>
	<array>
		<dict>
			<key>CFBundleTypeRole</key>
			<string>Editor</string>
			<key>CFBundleURLSchemes</key>
			<array>
				<string>${KAKAO_API_KEY}</string>
			</array>
		</dict>
    </array>
~~~
