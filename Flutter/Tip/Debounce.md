# Debounce
n초 동안 대기를 한 후에 코드를 실행하고 싶을때 사용   
ex) 몇초동안 사용자가 TextField에 입력이 없을시 다음 함수를 실행 

## 예시 코드
아래 예제에선 0.5초가 기본 초로 제시.
### 정의
~~~
import 'dart:async';

import 'package:flutter/material.dart';

class Debounce {
  final int milliseconds;
  Debounce({
    this.milliseconds = 500,
  });

  Timer? _timer;

  void run(VoidCallback action) {
    if (_timer != null) {
      _timer!.cancel();
    }

    _timer = Timer(Duration(milliseconds: milliseconds), action);
  }
}
~~~

### 사용
위에서
~~~
final debounce = Debounce(milliseconds: 1000);
~~~
정의(인스턴스로 만든) 후 아래처럼 사용
~~~
debounce.run(() {
  context.read<TodoSearchCubit>().setSearchTerm(newSearchTerm);
});
~~~