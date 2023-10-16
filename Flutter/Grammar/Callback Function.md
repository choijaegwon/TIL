# Callback Function

## 예시 코드
~~~
void main() {
  final sayHi = (name) => 'Hi, $name';
  welcome(sayHi, 'Andrea');
}

void welcome(String Function(String) greet,
             String name) {
  print(greet(name));
  print('Welcome to this course');
}
~~~

![Untitled](https://github.com/choijaegwon/choijaegwon.github.io/assets/68246962/1d95c94e-58ca-4526-873a-e556f5a5bdf2)

# Reference
https://codewithandrea.com/tips/dart-flutter-easy-wins-36-42/#41-anonymous-functions-can-be-assigned-to-variables-or-passed-as-arguments-to-other-functions   
