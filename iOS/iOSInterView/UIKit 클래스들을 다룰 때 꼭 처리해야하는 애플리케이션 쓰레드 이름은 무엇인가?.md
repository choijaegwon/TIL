# UIKit 클래스들을 다룰 때 꼭 처리해야하는 애플리케이션 쓰레드 이름은 무엇인가?

## Main Thread
- Cocoa Touch 앱에서는 UIApplication의 인스턴스가 main thread에 붙기 때문입니다. UIApplication은 앱을 시작할 때 인스턴스화 되는 앱의 첫번째 부분인데 앱의 run loop를 포함하여 main event loop를 설정하고 event 처리를 시작합니다. 앱의 main even loop는 touch, gesture등의 모든 UI Event를 수신합니다.
