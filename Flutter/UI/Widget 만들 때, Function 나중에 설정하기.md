# Widget 만들 때, Function 나중에 설정하기

일단 기능을 만들어두고, 나중에 혹은, 각기다른 기능을 만들어 주고 싶을때가 있다.  
그럴 땐 이런식으로

~~~
class FunctionTestView extends StatelessWidget {
  void Function()? gestureFunction;

  FunctionTestView({
    this.gestureFunction,
  });

  @override
  Widget build(BuildContext context) {
    return GestureDetector(
      onTap: gestureFunction,
      child: Container(
        height: 100,
        color: Colors.amber,
      ),
    );
  }
}
~~~

추후에 함수를 받을 거라고 선언해주고,

~~~
FunctionTestView(
  gestureFunction: () {
    log('뷰 클릭 테스트');
  },
),
~~~

이런 식으로사용해주면 필요할 때, 함수를 선언해 줄 수 있다.