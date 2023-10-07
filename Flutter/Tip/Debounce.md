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

## 예시 코드2
RxDart를 사용하면
Bloc.dart 에서
~~~
 EventTransformer<SetSearchTermEvent> debounce<SetSearchTermEvent>(
      Duration duration) {
    return (events, mapper) => events.debounceTime(duration).flatMap(mapper);
  }
~~~
를 정의한후

on<T> 이벤트 에 agrement로 추가해 줄 수있다.
~~~
on<SetSearchTermEvent>(
      (event, emit) {
        emit(state.copyWith(searchTerm: event.newSearchTerm));
      },
      transformer: debounce(Duration(milliseconds: 2000)),
    );
~~~
이러면 따로 예시 코드1 에서 처럼 작성 안해도 된다.