# Getters and Setters

## 예시 코드

~~~
int get _maxRpm = -100;
set setMaxRpm(int _maxRpm) => _maxRpm = rmp;
~~~

만약 입력값이 nullable이면
~~~
String? _name;
String? get name => (_name == null) ? 'Choi' : _name;
set setName(String? name) => (name == null) ? _name = 'Gwon' : _name = name;
~~~

~~~
class Temperature {
  Temperature.celsius(this.celsius);
  Temperature.fahrenheit(double fahrenheit)
    : celsius = (fahrenheit - 32) / 1.8;
  double celsius;
  double get fahrenheit
    => celsius * 1.8 + 32;
  set fahrenheit(double fahrenheit)
    => celsius = (fahrenheit - 32) / 1.8;
}

final temp1 = Temperature.celsius(30);
print(temp1.fahrenheit);
final temp2 = Temperature.fahrenheit(90);
temp2.celsius = 28;
~~~

# Reference  
https://codewithandrea.com/videos/top-dart-tips-and-tricks-for-flutter-devs/#9-getters-and-setters