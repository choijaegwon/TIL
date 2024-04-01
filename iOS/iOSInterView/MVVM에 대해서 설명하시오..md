# MVVM에 대해서 설명하시오.

## MVVM

- MVVM은 iOS 에서 가장 많은 인기를 누리고 있다. Model - View - ViewModel 의 줄임표현이다.
- ViewModel은 테스트가 가능하기에 꽤나 쓸만하고, 이 모델 내부엔 UIKit 관련 코드가 없다. 즉, 뷰 모델은 ViewController 로딩과 의존성이 없기에 ViewModel에서 비즈니스 로직 테스트가 가능하다.
- UIViewController와 UIView는 함께 View로 분류된다.
- MVVM을 꼭 FRP(Function Reactive Programming) 구조로 작성할 필요는 없다. 즉, MVVM 아키텍쳐에게 Rx, ReactiveCocoa가 필수 라이브러리는 아니다. 그러나 이것의 부재가 MVVM의 단점인 많은 기반 코드 작성으로 귀결된다. 대체로Rx가 바인딩을 돕기 위한 라이브러리로 사용된다.
- MVVM의 가장 큰 장점은 테스트의 용이성에 있다. 다만 VIPER의 Router 역할 없이, 어떻게 뷰 컨트롤러와 바인딩할 수 있을지가 문제로 남는다. Apple은 이를 위해 의존성 주입을 권장했으나, 이는 꽤나 문제적이다.

## MVVM 의존성 주입의 문제

만약 뷰컨 A에 뷰컨 B의 의존성을 주입하고 다시 뷰컨 C의 의존성을 주입하면, 뷰컨 A는 모든 뷰컨의 의존성을 갖게 된다. 앱 하나가 갖는 NavigationController 의 수만큼이나 이런 현상은 많이 발생할 수 있다. 가독성이 매우 떨어지고 실제로 필요한 것과 필요 없는 것이 무엇인지 구분하기에 어렵다.

버튼 하나만 눌렀는데, 그 내부에 Child 뷰컨이 또 다른 객체 의존성을 갖고 생성되고 if문으로 디바이스 상태에 따라 또 서로 다른 뷰컨과 보여주기 방식이 작성되고 있다. 이처럼 Router의 부재는 MVVM의 테스트 용이성에 걸림돌이 된다.

~~~
func doneButtonTapped() {
    let vc = ChildViewController(prepareNeccessaryState())

    if Device.isIPad() {
        navigationController.pushViewController(vc, animated: true, completion: nil)
    } else {
        var nav = UINavigationController(rootViewController: vc)
        nav.modalPresentationStyle = UIModalPresentationStyle.Popover
        var popover = nav.popoverPresentationController
        popoverContent.preferredContentSize = CGSizeMake(500,600)
        popover.delegate = self
        popover.sourceView = self.view
        popover.sourceRect = CGRectMake(100, 100, 0, 0)

        presentViewController(nav, animated: true, completion: nil)
    }
}
~~~

## MVVM과 Router의 부재

Router 하나의 부재로 인해 적어도 2개의 문제가 발생하고 있다. VIPER에서 Router 는 자기 자신 내부에서 각 뷰로 넘어가기 위한 로직을 소화한다. 필요한 만큼의 의존성 주입이 이루어진다. 그러나 MVVM은 뷰를 어떻게 넘기고 보여줄지를 담당하는 Router가 없기에 아래와 같은 문제가 발생한다.

- 불필요한 의존성 발생 
    - 대체 하나의 뷰컨이 몇 개의 뷰컨과 관계를 맺고 있는 것인가.
- 테스트 용이성 저하 
    - 뷰 모델 테스트를 위해 뷰 컨을 stub해야 한다.
- 재사용성 저하
- 유지보수 어려움

## MVVM의 한계 극복

Router가 없다면, 만들면 된다. 이를 위한 Flow Coordinators 패턴이 준비되어 있다. 이제 MVVM에서도 하나의 뷰 컨트롤러를 이곳저곳에서 더 편하게 재활용할 수 있다. 위에서 나온 코드를 이제 다 지워버리고 이렇게 해보자. 이제 함수를 통해서 의존성을 필요한 만큼만 주입할 것이다.

~~~
class MyViewController {
  let onDone = (Void -> Void)?

  func doneButtonTapped() {
    onDone?(prepareNeccesaryState())
  }
}
~~~
뷰컨, 뷰모델은 다른 화면을 참조하지 않을 것이고, UIKit 뷰를 그리는 객체나 메소드를 쓸 필요가 없어진다. Delegate 처럼 작동할 수 있을 것이며, 싱글톤 참조도 필요하지 않다. 테스트 코드도 아래처럼 간단해질 것이다