# FCM
- Firebase Cloud Messaging의 약자  
- 파이어베이스를 이용한 푸시 알림

## 사용법  

### Apple 
P8 인증서 받기(https://developer.apple.com/account/)  
![image](https://user-images.githubusercontent.com/68246962/232309127-26efe7c4-9cf7-4eb6-a093-d1c684005260.png)  
Apple Push Notifications service(APNs) 체크  
![image](https://user-images.githubusercontent.com/68246962/232309232-f7cb1a6d-ecd2-41fc-8846-508381f4e326.png)  
![image](https://user-images.githubusercontent.com/68246962/232309430-ed7b0f88-3c3d-45b9-a87a-a253a1c79d97.png)  
다운로드 후 인증서 로컬에 저장하기  
키 ID복사 해두기

### 파이어베이스 
![image](https://user-images.githubusercontent.com/68246962/232309640-1545e1da-70c1-443e-9bab-9adf47894368.png)  
![image](https://user-images.githubusercontent.com/68246962/232309708-42816123-6c60-4c7f-a6af-f10d1e256ce8.png)  
앱 구성에서 Bundle Identifier 추가하기    
GoogleServices-Info.plist 다운받고  
다운 받은 파일은 바로 프로젝트에 넣어주기  

Cloud Messaging으로 이동 APNs 인증서 업로드  
![image](https://user-images.githubusercontent.com/68246962/232309841-d8313682-8b26-4303-999e-4316ea7659ca.png)  

- P8 파일 다운로드
- P8 파일의 KeyID입력(파일명의 숫자)
- Apple 회원 ID 입력

### Xcode
SPM or Pod 사용해서 패키지 추가
- FirebaseMessaging
- FirebaseAnalytics

Info.plist
~~~
FirebaseAppDelegateProxyEnabled
~~~
추가 값은 0 
![image](https://user-images.githubusercontent.com/68246962/232310070-7a5f26e5-2107-4b64-b9f0-36507d8040c6.png)  
Xcode 프로젝트 설정누르고 Signing & Capabilities.로 이동  
![image](https://user-images.githubusercontent.com/68246962/232310535-c1494ddc-e491-4627-8d53-ee146c84b177.png)  
에서 Push Notifications추가  


## 예시코드

AppDelegate.swift
~~~
import Firebase
import FirebaseMessaging
import FirebaseAnalytics

class AppDelegate: UIResponder, UIApplicationDelegate {
	func application(
        _ application: UIApplication,
        didFinishLaunchingWithOptions _: [UIApplication.LaunchOptionsKey: Any]? = nil
    ) -> Bool {
  
	// 파이어베이스 설정
	FirebaseApp.configure()

	// 디버그에 표시되는 양 줄이기
	FirebaseConfiguration.shared.setLoggerLevel(.min)
	
  // 메세징 델리겟
	Messaging.messaging().delegate = self

	// 원격 알림 설정
	let authOptions: UNAuthorizationOptions = [.alert, .badge, .sound]
  UNUserNotificationCenter.current().requestAuthorization(options: authOptions, completionHandler: { _, _ in})
  application.registerForRemoteNotifications()

	// 푸시 포그라운드 설정
	UNUserNotificationCenter.current().delegate = self

	return true
}

// MARK: UNUserNotificationCenterDelegate(알람설정)

extension AppDelegate: UNUserNotificationCenterDelegate {
    func userNotificationCenter(
        _: UNUserNotificationCenter,
        willPresent _: UNNotification,
        withCompletionHandler completionHandler: @escaping (UNNotificationPresentationOptions) -> Void
    ) {
        completionHandler([.banner, .sound])
    }

    func userNotificationCenter(
        _: UNUserNotificationCenter,
        didReceive _: UNNotificationResponse,
        withCompletionHandler completionHandler: @escaping () -> Void
    ) {
        completionHandler()
    }

		// 기기 토큰 등록
    func application(
        _: UIApplication,
        didRegisterForRemoteNotificationsWithDeviceToken deviceToken: Data
    ) {
        Messaging.messaging().apnsToken = deviceToken
    }
}

// MARK: MessagingDelegate

extension AppDelegate: MessagingDelegate {
    func messaging(
        _: Messaging,
        didReceiveRegistrationToken fcmToken: String?
    ) {
        print("Firebase registration token: \(String(describing: fcmToken))")

        let dataDict: [String: String] = ["token": fcmToken ?? ""]
        NotificationCenter.default.post(
            name: Notification.Name("FCMToken"),
            object: nil,
            userInfo: dataDict
        )
        // TODO: If necessary send token to application server.
        // Note: This callback is fired at each app startup and whenever a new token is generated.
				// 토큰 저장하는 코드
        // ex)MyAuth.default.registrationToken = fcmToken ?? ""
    }

}
~~~

# Reference
https://firebase.google.com/docs/cloud-messaging/ios/client?hl=ko  
https://www.kodeco.com/20201639-firebase-cloud-messaging-for-ios-push-notifications  
