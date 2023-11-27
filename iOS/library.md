# library

### [SnapKit]-코드로 작성시 까다로운 뷰 작업이나, 계속해서 뷰 모양이 바뀌는 경우에 사용하는 라이브러리

https://github.com/SnapKit/SnapKit

~~~
pod 'SnapKit'
~~~

### [Then]-코드로 UI작성할때, 코드를 줄여주는 라이브러리

https://github.com/devxoul/Then

~~~
pod 'Then'
~~~

### [Alamofire]-iOS에 네트워킹 단계를 개발하며 설치하는 라이브러리

https://github.com/Alamofire/Alamofire

~~~
pod 'Alamofire'
~~~

### [SwiftyJSON]-Json을 쓰기 쉽게 만든 라이브러리

https://github.com/SwiftyJSON/SwiftyJSON

~~~
pod 'SwiftyJSON'
~~~

### [SDWebImage]-URL 이미지 다운로드받고, 이후 캐싱사용하는 라이브러리

https://github.com/SDWebImage/SDWebImage

~~~
pod 'SDWebImage'
~~~

### [TweeTextField]-로그인, 패스워드할때 글 올라오고 내려가는 라이브러리

https://github.com/oleghnidets/TweeTextField

~~~
pod 'TweeTextField'
~~~

### [IQKeyboardManager]-글작성할때, 키보드 올라오고내려가는거 자동으로 길이측정해주는라이브러리

https://github.com/hackiftekhar/IQKeyboardManager

~~~
pod 'IQKeyboardManagerSwift'
~~~

### [SwipeCellKit]-스와이프 기능 만들때 사용하는 라이브러리

https://github.com/SwipeCellKit/SwipeCellKit

~~~
pod 'SwipeCellKit'
~~~

### [BonMot]-Label에 속성넣을때 어트리뷰트대신 사용하면 좋은 라이브러리

https://github.com/Rightpoint/BonMot

~~~
pod 'BonMot'
~~~

### [Cosmos]-별점기능 라이브러리

https://github.com/evgenyneu/Cosmos

~~~
pod 'Cosmos'
~~~

### [MGStarRatingView]-별점기능 라이브러리

https://github.com/magi82/MGStarRatingView

~~~
pod 'MGStarRatingView'
~~~

### [ActiveLabel]-맨션, 해쉬태그, URL등을 활용가능한 라이브러리

https://github.com/optonaut/ActiveLabel.swift

~~~
pod 'ActiveLabel'
~~~

### [Realm]-내부 저장소 사용하는 라이브러리
https://github.com/realm/realm-swift

~~~
pod 'RealmSwift'
~~~

### RealmStudio파일

[RealmStudio](https://studio-releases.realm.io/latest/download/mac-dmg)  
[1:N 설정 방법](https://apcheon.tistory.com/132)

## 데이터 확인하는 방법

Appdelegate.swift

~~~
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool { 
    print(Realm.Configuration.defaultConfiguration.fileURL)
}
~~~
Realm Studio를 연후  
command + shift + G 를 누르고 print된 경로를 복사 붙여 넣기  
default.realm 파일 확인   

### [FSCalendar]-달력 라이브러리

https://github.com/WenchaoD/FSCalendar

~~~
pod 'FSCalendar'
~~~

### [CLTypingLabel]-한글자한글자 나타나는 라이브러리

https://github.com/cl7/CLTypingLabel

~~~
pod 'CLTypingLabel'
~~~

### [Firebase]

https://github.com/firebase/firebase-ios-sdk
| 서비스 또는 제품 | 포드 |
| --- | --- |
| https://firebase.google.com/docs/admob/ios/quick-start | pod 'Google-Mobile-Ads-SDK' |
| https://firebase.google.com/docs/analytics/get-started?platform=ios | pod 'FirebaseAnalytics' |
| https://firebase.google.com/docs/app-check | pod 'FirebaseAppCheck' |
| https://firebase.google.com/docs/app-distribution/set-up-alerts | pod 'FirebaseAppDistribution' |
| https://firebase.google.com/docs/auth/ios/start | pod 'FirebaseAuth' |
| https://firebase.google.com/docs/firestore/quickstart | pod 'FirebaseFirestore' |
| https://firebase.google.com/docs/functions | pod 'FirebaseFunctions' |
| https://firebase.google.com/docs/cloud-messaging/ios/client | pod 'FirebaseMessaging' |
| https://firebase.google.com/docs/storage/ios/start | pod 'FirebaseStorage' |
| https://firebase.google.com/docs/crashlytics/get-started?platform=ios | pod 'FirebaseCrashlytics' |
| https://firebase.google.com/docs/dynamic-links/ios/create | pod 'FirebaseDynamicLinks' |
| https://firebase.google.com/docs/in-app-messaging/get-started?platform=ios | pod 'FirebaseInAppMessaging' |
| https://firebase.google.com/docs/projects/manage-installations | pod 'FirebaseInstallations' |
| https://firebase.google.com/docs/ml | pod 'FirebaseMLModelDownloader' |
| https://firebase.google.com/docs/perf-mon/get-started-ios | pod 'FirebasePerformance' |
| https://firebase.google.com/docs/database/ios/start | pod 'FirebaseDatabase' |
| https://firebase.google.com/docs/remote-config/get-started?platform=ios | pod 'FirebaseRemoteConfig' |

### [Chameleon]-앱 색상 정해주는 라이브러리

https://github.com/vicc/chameleon

~~~
pod 'ChameleonFramework/Swift'
~~~

### [DLRadioButton]-**RadioButton버튼 쉽게 만드는 라이브러리**

https://github.com/DavydLiu/DLRadioButton

~~~
pod 'DLRadioButton'
~~~

### [UITextView-Placeholder]-`UITextView에 placeholder 편하게 구현할수있는 라이브러리`

https://github.com/devxoul/UITextView-Placeholder

~~~
pod 'UITextView+Placeholder'
~~~

### [RxSwift]-Rx를 사용하고싶을때 사용하는 라이브러리

https://github.com/ReactiveX/RxSwift

~~~
pod 'RxSwift'
pod 'RxCocoa'
~~~

### [RxRealm]-Realm과 Rx를 함께 사용하고 싶을때 사용하는 라이브러리

https://github.com/RxSwiftCommunity/RxRealm

~~~
pod "RxRealm"
~~~

### [RxRealm]-Realm과 Rx를 함께 사용하고 싶을때 사용하는 라이브러리

https://github.com/RxSwiftCommunity/RxRealm

~~~
pod "RxRealm"
~~~

### [Toast-Swift]-Toast Message를 쉽게 만들어주는 라이브러리

https://github.com/scalessec/Toast-Swift

~~~
pod 'Toast-Swift'
~~~